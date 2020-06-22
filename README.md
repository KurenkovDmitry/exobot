python -m pip install vk_api
# exobot
python -m pip install vk_api
import vk_api
from vk_api.longpoll import VkLongPoll, VkEventType
def write_msg(user_id, message):
    vk.method('messages.send', {'user_id': user_id, 'message': message})

token = "42a5e447d41314e4dcc0b89782429d8a6cea3b63304c8633d5390b8cfde2d6dfa8392ce31887ba43dd035"

vk = vk_api.VkApi(token=token)

longpoll = VkLongPoll(vk)

for event in longpoll.listen():
    if event.type == VkEventType.MESSAGE_NEW
        if event.to_me:
            request = event.text
            write_msg(event.user_id, request)
