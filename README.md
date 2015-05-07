**Quick start - Example**

 - Clone this repository
 - Go to root directory of this repository
 - Install rabbitmq (server - when you get errors go to rabbitmq doc)
```bash
sudo apt-get install rabbitmq-server
```
 - Create virtual enviroment
```bash
virtualenv venv
``` 
 - Activate virtualev
```bash 
source venv/bin/activate
```
 - Go to src directory:
```bash
cd src
```
 - Install required software
```bash
pip install -r requirements.txt
```
 - In new terminal window (activate virtual venv)
```bash
source ../venv/bin/activate
```
> - Or run with pypy:
> ```bash 
virtualenv -p pypy venv-pypy
````
> ```bash 
. venv-pypy/bin/activate
````

 - Run task backend
```bash
celery -A tasks worker --loglevel=info
```


 - Back to first terminal window and run python interpreter
```bash
python
```
 - test script (put it in terminal which run python)
```python
In [1]: import tasks

In [2]: t = tasks.add.delay(2,3)

In [3]: d = tasks.add.AsyncResult(t.task_id)

In [4]: d.get()
Out[4]: 5 # you should get this result
``` 
