## s3url  - provide path. get url.
### A CLI tool to get a public link for any file

Uses [s3](http://aws.amazon.com/s3/) to store the files. It's a cool uploading tool that I've been using on my website and this is a hack on top of it.

#### Use Cases

- You need a quick way to send a file to someone. Instead of attaching it to an email or starting up your FTP server, use this to get a public URL.

- Another tool in your arsenal of `scp`, yousendit, and flash drives for quickly exchanging files.

#### Usage

You provide a path, it returns a URL

    s3url bucket-name path/to/file
    echo 'test' | s3url bucket-name filename

It also tries to use `pbcopy` on a mac, `xsel` or `xclip` on Linux to put the url into your clipboard.

<img src="https://raw.github.com/thrashr888/s3url/master/static/example.png">

#### Installation

    sudo curl https://raw.github.com/thrashr888/s3url/master/s3url -o /usr/local/bin/s3url;
    sudo chmod +x /usr/local/bin/s3url

Place AWS credentials in ~/.awssecret, for (fake) example:

    $ cat ~/.awssecret
    13UEGMT5D34KE3MSFN38
    fLYs6+Je1yz2VRWOZknfcKiTs0wonZOC97biDLz0
    

Enable Clipboard Access (Only necessary on Linux)

    sudo apt-get install xclip

I'll submit it to `brew` and `apt-get` if enough people are interested.

<img src="https://raw.github.com/thrashr888/s3url/master/static/install.png">

#### Notes

It uses S3 as a storage backend. Idea blatantly stolen from [geturl](https://github.com/uams/geturl). Most code taken from the [official AWS PHP SDK](http://aws.amazon.com/php/).