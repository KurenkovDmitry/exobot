import random

import vk_api
from vk_api.longpoll import VkLongPoll, VkEventType

from commander.commander import Commander

def write_msg(user_id, message):
    vk.method('messages.send', {'user_id': user_id, 'message': message, 'random_id': random.randint(0, 2048)})

token = "42a5e447d41314e4dcc0b89782429d8a6cea3b63304c8633d5390b8cfde2d6dfa8392ce31887ba43dd035"

vk = vk_api.VkApi(token=token)

longpoll = VkLongPoll(vk)

commander = Commander()

print("Бот запущен")

for event in longpoll.listen():

    # Если пришло новое сообщение
    if event.type == VkEventType.MESSAGE_NEW:

        # Если оно имеет метку для меня( то есть бота)
        if event.to_me:

            # Сообщение от пользователя
            request = event.text
            write_msg(event.user_id, request)
