## Welcome to my Unity Music Player! (A prototype)

### Project Description
This Unity Music was created as an exercise for Object-Oriented Programming and utilizes Unity ver. 2020.1.17f1! <br />
The original was created by YouTube user: xOctoManx on Aug 19, 2017. <br />
His tutorial is here: https://www.youtube.com/watch?v=zpiwhC8zp4A <br />

I built on what he taught in his tutorial by adding dynamic song titles and album covers.

### Resolution
920 x 600px

Try the player [here](https://hue-n.github.io/Unity-Music-Player/)!

### Music Credits:
Hue-n: Crystalization Cave, Challenge of the Stars <br />
Ubitsoft, Rayman 3 Original Soundtrack: Curious Globox <br />
Groove Armada: Madder <br />

### How Object-Oriented Programming was incorporated:

= A "Song" class was created that holds the data for the song
```C#
public class Song : MonoBehaviour
{
    //Song Variables Here

    public string songName;

    public AudioClip song;

    public int songID;

    public Sprite songImage;
}
```

- The Audio Manager then creates an array of these Songs and parses their data in their respective methods.
- The array is accessed through the "currentTrack" int.
```C#
    #region Variables
    public GameObject[] songList; //Tracklist
    
    ...
    
    public void NextTitle() //add next song into queue
    {
        source.Stop();
        currentTrack++;

        if (currentTrack > songList.Length - 1)
        {
            currentTrack = 0;
        }
        source.clip = songList[currentTrack].GetComponent<Song>().song;
        source.Play();
        
    ...
    
        void ShowCurrentTitle()
    {
        clipTitleText.text = "♪ " + songList[currentTrack].GetComponent<Song>().songName;
        fullLength = (int)source.clip.length;
        clipTitleText2.text = songList[currentTrack].GetComponent<Song>().songName;

    }
    
    ...
    
    void ShowCurrentAlbumCover()
    {
        albumCover.GetComponent<Image>().sprite = songList[currentTrack].GetComponent<Song>().songImage;
    }
```
