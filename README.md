# machinelearning
from googleapiclient.discovery import build
def youtube_search(search):
  youtube = build("youtube","v3",developerKey="AIzaSyChZlElpPxpaAnycO-HUuP0uCZUtHkC10o")
  search_response = youtube.search().list(q=search,part="id,snippet",maxResults=5).execute()
  for search_result in search_response.get('items', []):
    if search_result['id']['kind'] == 'youtube#video':
      print(u"%s" % (search_result['snippet']['title']))
  print(100*"=",end="\n\n")
if __name__=="__main__":
  while True:
    print(100*"=")
    search = input("search >")
    if search=="q":
      break
    youtube_search(search)
