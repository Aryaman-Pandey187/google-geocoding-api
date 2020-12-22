# Simplified-Google MAPS
This app takes the address of the place that you want to go as input and then a gives a link as output. The link automatically gets copied to the clipboard.Then on pasting the link in any browser the user will be directed to google maps and it will show the way to the place from your crurent location.
Here is the code:


    import requests
    import json
    import pyperclip
    api_key = ' '    #Don't forget to insert own your API key 
    address = input('Enter Address:')
    params = {
        'key': api_key,
        'address': address
    }
    url = 'https://maps.googleapis.com/maps/api/geocode/json?'
    response = requests.get(url, params=params).json()
    latitude = response['results'][0]["geometry"]['location']['lat']
    longitude = response['results'][0]["geometry"]['location']['lng']
    link = 'http://www.google.com/maps/place/'
    maps_link = link + str(latitude) +"," +  str(longitude)
    pyperclip.copy(maps_link)
    spam = pyperclip.paste()
    print(maps_link)
    print("This link has been copied to clipboard")
    input("Press any key to exit")
