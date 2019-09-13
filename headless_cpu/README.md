# Usage #
    Xvfb :0 -ac -screen 0 1024x768x24 &
    export DISPLAY=:0
    python3 render.py