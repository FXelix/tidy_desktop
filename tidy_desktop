
# sort your desktop; jpg's, mp3's etc!

import os
import re
import shutil
import getpass
import sys
import time


def tidy_desktop():
    username = getpass.getuser()  # Get the logged in username
    desktop = os.path.join("C:\\","Users", username, "Desktop")  # desktop path
    desktop_content = os.listdir(desktop)

    img_pattern = r"([-\]\[\)\(\w\s]+\.png |" \
                  r"[-\]\[\)\(\w\s]+\.jp[e]?g |" \
                  r"[-\]\[\)\(\w\s]+\.gif)"

    music_pattern = r"([-\]\[\)\(\w\s]+\.mp3|" \
                    r"[-\]\[\)\(\w\s]+\.avi|" \
                    r"[-\]\[\)\(\w\s]+\.wav)"

    img_compile = re.compile(img_pattern, re.X | re.I)     #  match images with pattern
    music_compile = re.compile(music_pattern, re.X | re.I) #  match music files with patttern

    images = img_compile.findall(",".join(desktop_content))  # Turns all images into a string to match basename
    music = music_compile.findall(",".join(desktop_content)) # Turns all songs into a string to match basename

    print("-"*32)
    if not images:
        print("No images found on your Desktop.")
    else:
        for img in images:
            img_path = os.path.join("C:\\Users\\{}\\Desktop\\{}".format(username, img))  # get the path
            shutil.move(img_path, "C:\\Users\\{}\\Pictures".format(username))                 # move to Pictures
            print("Moved {} to Pictures.".format(img))

    if not music:
        print("No music found on your Desktop.")
    else:
        for song in music:
            music_path = os.path.join("C:\\Users\\{}\\Desktop\\{}".format(username, song))  # get the path
            shutil.move(music_path, "C:\\Users\\{}\\Music".format(username))                     # move to Music
            print("Moved {} to Music.".format(song))
    print("-"*32)
    time.sleep(2)
    sys.exit(1)

if __name__ == "__main__":
    tidy_desktop()
