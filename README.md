# rosyid
import requests

def get_weather(city):
    api_key = "5fcecfa19065b9593b87735917c5c2ea"
    url = "https://api.openweathermap.org/data/2.5/weather"
    
    params = {
        "q": city,
        "appid": api_key,
        "units": "metric"
    }

    response = requests.get(url, params=params)

    if response.status_code == 200:
        data = response.json()
        print(f"Cuaca di {city}: {data['weather'][0]['description']}")
        print(f"Temperatur: {data['main']['temp']}°C")
        print(f"Kelembaban: {data['main']['humidity']}%")
        print(f"Kecepatan angin: {data['wind']['speed']} m/s")
    else:
        print("Gagal mendapatkan data cuaca!")

if __name__ == "__main__":
    city = input("Masukkan nama kota: ")
    get_weather(city)
