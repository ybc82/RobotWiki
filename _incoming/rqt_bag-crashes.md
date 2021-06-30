# rqt_bag crashes when displaying certain raw messages

rqt_bag crashed when trying to display raw messages. The traceback is as following:

```bash
Traceback (most recent call last):
  File "/opt/ros/kinetic/lib/python2.7/dist-packages/rqt_bag/plugins/message_view.py", line 93, in event
    self.message_viewed(bag, msg_data)
  File "/opt/ros/kinetic/lib/python2.7/dist-packages/rqt_bag/plugins/raw_view.py", line 73, in message_viewed
    self.message_tree.set_message(msg)
  File "/opt/ros/kinetic/lib/python2.7/dist-packages/rqt_bag/plugins/raw_view.py", line 115, in set_message
    self._add_msg_object(None, '', '', msg, msg._type)
  File "/opt/ros/kinetic/lib/python2.7/dist-packages/rqt_bag/plugins/raw_view.py", line 249, in _add_msg_object
    self._add_msg_object(item, subpath, subobj_name, subobj, subobj_type)
  File "/opt/ros/kinetic/lib/python2.7/dist-packages/rqt_bag/plugins/raw_view.py", line 206, in _add_msg_object
    obj_repr = codecs.utf_8_decode(str(obj).encode(), 'ignore')[0]
UnicodeDecodeError: 'ascii' codec can't decode byte 0xfc in position 1: ordinal not in range(128)

```

I also found out that rqt_bag only crashes when I tried to display uint8[]. uint8[] is treated as string in raw_view.py. Not sure where this happened. Because the raw_view.py is encoding/decoding it using utf-8, it crashes when there is an incompatible uint8. No idea why 'ignore' option doesn't solve the problem.

One way to solve the problem is as following: Add a branch for strings, where no decoding or encoding happens. The drawback is that you can't read the uint8[] from rqt_bag. It would be better to decode the obj as uint8[] but that will require further understanding of python and rqt_bag source code.

```python
        elif type(obj) in [bool, int, long, float, complex, rospy.Time]:
            obj_repr = codecs.utf_8_decode(str(obj).encode(), 'ignore')[0]

            # Truncate long representations
            if len(obj_repr) >= 50:
                obj_repr = obj_repr[:50] + '...'

            label += ': ' + obj_repr

        elif type(obj) in [str]:
            # Ignore any binary data
            obj_repr = str(obj)
            #obj_repr = codecs.utf_8_decode(str(obj).encode(), 'ignore')[0]

            # Truncate long representations
            if len(obj_repr) >= 50:
                obj_repr = obj_repr[:50] + '...'

            label += ': ' + obj_repr  
```

Environment: ROS Kinetic, python 2.