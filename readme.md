## s3url  - provide path. get url.
### A CLI tool to get a public link for any file

Uses [Amazon S3](http://aws.amazon.com/s3/) to store the files. s3url copies files and streams to a public S3 file and copies the url to your clipboard. A file sharing app for Amazon S3.

#### Use Cases

- You need a quick way to send a file to someone. Instead of attaching it to an email or starting up your FTP server, use this to get a public URL.

- Another tool in your arsenal of `scp`, yousendit, and flash drives for quickly exchanging files.

#### Usage

You provide a path, it returns a URL

    s3url bucket-name path/to/file
    echo 'test' | s3url bucket-name filename

It also tries to use `pbcopy` on a mac, `xsel` or `xclip` on Linux to put the url into your clipboard.

Example output:

    $ s3url my-bucket test.txt
    Uploading File 'test.txt' to S3 Bucket 'my-bucket'...
    
    A Public Share URL for: test.txt
    http://my-bucket.s3.amazonaws.com/test.txt
    
    Also in your clipboard.

#### Installation

    sudo curl https://raw.github.com/thrashr888/s3url/master/s3url -o /usr/local/bin/s3url;
    sudo chmod +x /usr/local/bin/s3url

Place AWS credentials in ~/.awssecret, for (fake) example:

    $ cat ~/.awssecret
    13UEGMT5D34KE3MSFN38
    fLYs6+Je1yz2VRWOZknfcKiTs0wonZOC97biDLz0
    

Enable Clipboard Access (Only necessary on Linux):

    sudo apt-get install xclip

#### Notes

It uses S3 as a storage backend. Idea and readme copy blatantly stolen from [geturl](https://github.com/uams/geturl). S3 code taken from the [official AWS PHP SDK](http://aws.amazon.com/php/).
