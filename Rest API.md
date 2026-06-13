"[https://www.youtube.com/playlist?list=PLXmMXHVSvS-CoYS177-UvMAQYRfL3fBtX](https://www.youtube.com/playlist?list=PLXmMXHVSvS-CoYS177-UvMAQYRfL3fBtX) rest apis bauen, evtl. nur die ersten 2 3 Videos schauen"

"allgemeine Einfuehrung: zuerst schauen! [https://www.youtube.com/watch?v=7YcW25PHnAA](https://www.youtube.com/watch?v=7YcW25PHnAA)"

"[https://youtu.be/Q-BpqyOT3a8](https://youtu.be/Q-BpqyOT3a8) ausfuehrlich, nur wenn du Lust hast oder fuer irgendwann"

"um APIs abzufragen: evtl. am relevantesten nachzubauen [https://youtu.be/19-LOqdI61k](https://youtu.be/19-LOqdI61k)"

```
from flask import Flask
app = Flask(__name__)


@app.route('/')
def hello():
    return "Hello World!"

if __name__ == '__main__':
    app.run(port=8000)
```
