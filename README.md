# Import the necessary libraries
import requests
import json

# Set up the API endpoint and access token
endpoint = "https://api.instagram.com/v1/"
access_token = "YOUR_ACCESS_TOKEN"

# Make a GET request to retrieve user information
user_id = "USER_ID"
user_url = endpoint + "users/" + user_id + "/?access_token=" + access_token
response = requests.get(user_url)
user_data = json.loads(response.text)

# Print the user's username
print("Username:", user_data["data"]["username"])

# Make a GET request to retrieve user's recent media
media_url = endpoint + "users/" + user_id + "/media/recent/?access_token=" + access_token
response = requests.get(media_url)
media_data = json.loads(response.text)

# Print the user's recent media
print("Recent Media:")
for media in media_data["data"]:
    print("Media ID:", media["id"])
    print("Media Type:", media["type"])
    print("Media URL:", media["images"]["standard_resolution"]["url"])
    print()
