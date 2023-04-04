# QUIZ 052
![Screen Shot 2023-04-04 at 22 44 07](https://user-images.githubusercontent.com/111819437/229812308-745eaf6a-ca79-4a3c-b35a-af2a7d9f70a1.png)

## CODE
```.py
class MovieDownloader:
    def __init__(self, download_speed):
        if download_speed <= 0:
            # Check if download speed is greater than 0, if not, raise a ValueError with an appropriate error message.
            raise ValueError("Download speed must be greater than 0")
        self.download_speed = download_speed

    def calculate_download_time(self, movie_size):
        if movie_size <= 0:
            # Check if movie size is greater than 0, if not, raise a ValueError with an appropriate error message.
            raise ValueError("Movie size must be greater than 0")
        # Calculate download time in seconds 
        download_time_seconds = movie_size / (self.download_speed * 1024 * 1024)
        # Convert download time from seconds to minutes and seconds.
        minutes = int(download_time_seconds // 60)
        seconds = int(download_time_seconds % 60)
        # Return the download time as a string 
        return f"{minutes} minutes {seconds} seconds"
```
## EVIDENCE
![Screen Shot 2023-04-05 at 0 18 30](https://user-images.githubusercontent.com/111819437/229839332-e93adf16-1421-4aab-ad1f-7b276ad2221e.png)
