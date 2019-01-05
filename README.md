# downloadWZX下载王祖贤的照片
#coding:utf-8
import requests
import json
query = '王祖贤'
'''下载图片'''
def download(src,id):
    dir = './' + str(id) + '.jpg'
    try:
        pic = requests.get(src,timeout=)
    except requests.exceptions.ConnectionError:
        #print 'error, %d 当前图片无法下载', %id
        print('图片无法下载')
    fp = open(dir,'wb')
    fp.write(pic.content)
    fp.write(pic.content)
    fp.close()

'''for 循环 请求全部的 url'''
for i in range(0,22598,20):
    url = 'https://www.douban.com/j/search_photo?q=王祖贤&limit=20&start='+str(i)
    html = requests.get(url).text   # 得到返回结果
    response = json.loads(html,encoding='utf-8') # 将 JSON 个是转换成 Pyhon 对象
    for image in response['images']:
        print image['src'] # 查看当前下载图片的网址
        download(image['src'],image['id']) # 下载一张图片
