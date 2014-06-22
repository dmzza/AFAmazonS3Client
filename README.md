# AFAmazonS3Client

`AFAmazonS3Client` is an `AFHTTPRequestOperationManager` subclass for interacting with the [Amazon S3 API](http://aws.amazon.com/s3/).

As the S3 API returns XML responses, you may find it useful to set [AFOnoResponseSerializer](https://github.com/AFNetworking/AFOnoResponseSerializer) as the response serializer.

## Example Usage

```Objective-C
#import <AFAmazonS3Client/AFAmazonS3Manager.h>

AFAmazonS3Manager *s3Manager = [[AFAmazonS3Manager alloc] initWithAccessKeyID:@"..." secret:@"..."];
[[self.s3Manager requestSerializer] setRegion:AFAmazonS3USStandardRegion];
[[self.s3Manager requestSerializer] setBucket:@"..."];

[s3Manager postObjectWithFile:@"/path/to/file"
              destinationPath:@"https://s3.amazonaws.com/example"
                   parameters:nil
                     progress:^(NSUInteger bytesWritten, long long totalBytesWritten, long long totalBytesExpectedToWrite) {
                        NSLog(@"%f%% Uploaded", (totalBytesWritten / (totalBytesExpectedToWrite * 1.0f) * 100));
}
                      success:^(id responseObject) {
                        NSLog(@"Upload Complete");
}
                      failure:^(NSError *error) {
                         NSLog(@"Error: %@", error);
}];
```

## Contact

Mattt Thompson

- http://github.com/mattt
- http://twitter.com/mattt
- m@mattt.me

## License

AFAmazonS3Client is available under the MIT license. See the LICENSE file for more info.
