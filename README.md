# Firebase Cloud Messaging (FCM) API Documentation
Firebase Cloud Messaging (FCM) is a cross-platform messaging solution that lets you reliably send messages at no cost. Using FCM, you can notify a client app that new email or other data is available to sync. You can send notification messages to drive user re-engagement and retention.

## Step By Step Process for FCM Notification API Integration
  - First You need download Your Firebase Auth Json file form firebase console.
  - After that you need to visit [Open this Website](https://fcm.papayacoders.com) website And here You will get for to fill details and upload json file.
  - You Need to copy your project id from FCM json file and paste into input field.
  - And Upload JSON File filed your need to upload your json file which you downloaded from firebase
  - Now submit the form only one project Id can upload one time.
  - Now you need to click on top right corner Api documentation menu link
  - Now you can see Swagger Documentation for api.
  - You can see 3 api avaiable for send notice
    -- /api/send-token-notice
    -- /api/send-topic-notice
    -- send-notice/{projectname}/{fcmtype}/{token}/{type}

All Api have its own property You need to use according your need in the project

> Base Url = https://fcm.papayacoders.com

### Send FCM message Using token /api/send-token-notice
Using this Api you need to pass all thing in POST BODY

### Curl Code
```
curl --location 'https://fcm.papayacoders.com/api/send-token-notice' \
--form 'title="HELLLO"' \
--form 'message="HELLO TEST Token"' \
--form 'token="Enter your token"' \
--form 'projectname="project name which you enter form submit"'

```
### PHP code
```
$client = new Client();
$options = [
  'multipart' => [
    [
      'name' => 'title',
      'contents' => 'HELLLO'
    ],
    [
      'name' => 'message',
      'contents' => 'HELLO TEST Token'
    ],
    [
      'name' => 'token',
      'contents' => 'Enter your token'
    ],
    [
      'name' => 'projectname',
      'contents' => 'project name which you enter form submit'
    ]
]];
$request = new Request('POST', 'https://fcm.papayacoders.com/api/send-token-notice');
$res = $client->sendAsync($request, $options)->wait();
echo $res->getBody();

------------------------------

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://fcm.papayacoders.com/api/send-token-notice',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => array('title' => 'HELLLO','message' => 'HELLO TEST Token','token' => 'Enter your token','projectname' => 'project name which you enter form submit'),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
--------------------------
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://fcm.papayacoders.com/api/send-token-notice');
$request->setRequestMethod('POST');
$body = new http\Message\Body;
$body->addForm(array(
  'title' => 'HELLLO',
  'message' => 'HELLO TEST Token',
  'token' => 'Enter your token',
  'projectname' => 'project name which you enter form submit'
), array(

));
$request->setBody($body);
$request->setOptions(array());

$client->enqueue($request)->send();
$response = $client->getResponse();
echo $response->getBody();

```

### Dart Code
```
var data = FormData.fromMap({
  'title': 'HELLLO',
  'message': 'HELLO TEST Token',
  'token': 'Enter your token',
  'projectname': 'project name which you enter form submit'
});

var dio = Dio();
var response = await dio.request(
  'https://fcm.papayacoders.com/api/send-token-notice',
  options: Options(
    method: 'POST',
  ),
  data: data,
);

if (response.statusCode == 200) {
  print(json.encode(response.data));
}
else {
  print(response.statusMessage);
}

----------------------------

var request = http.MultipartRequest('POST', Uri.parse('https://fcm.papayacoders.com/api/send-token-notice'));
request.fields.addAll({
  'title': 'HELLLO',
  'message': 'HELLO TEST Token',
  'token': 'Enter your token',
  'projectname': 'project name which you enter form submit'
});


http.StreamedResponse response = await request.send();

if (response.statusCode == 200) {
  print(await response.stream.bytesToString());
}
else {
  print(response.reasonPhrase);
}

```
### Java code
```
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("text/plain");
RequestBody body = new MultipartBody.Builder().setType(MultipartBody.FORM)
  .addFormDataPart("title","HELLLO")
  .addFormDataPart("message","HELLO TEST Token")
  .addFormDataPart("token","Enter your token")
  .addFormDataPart("projectname","project name which you enter form submit")
  .build();
Request request = new Request.Builder()
  .url("https://fcm.papayacoders.com/api/send-token-notice")
  .method("POST", body)
  .build();
Response response = client.newCall(request).execute();
```
### Javascript
```
const formdata = new FormData();
formdata.append("title", "HELLLO");
formdata.append("message", "HELLO TEST Token");
formdata.append("token", "Enter your token");
formdata.append("projectname", "project name which you enter form submit");

const requestOptions = {
  method: "POST",
  body: formdata,
  redirect: "follow"
};

fetch("https://fcm.papayacoders.com/api/send-token-notice", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.error(error));

--------------------------------------

var form = new FormData();
form.append("title", "HELLLO");
form.append("message", "HELLO TEST Token");
form.append("token", "Enter your token");
form.append("projectname", "project name which you enter form submit");

var settings = {
  "url": "https://fcm.papayacoders.com/api/send-token-notice",
  "method": "POST",
  "timeout": 0,
  "processData": false,
  "mimeType": "multipart/form-data",
  "contentType": false,
  "data": form
};

$.ajax(settings).done(function (response) {
  console.log(response);
});

----------------------------------
// WARNING: For POST requests, body is set to null by browsers.
var data = new FormData();
data.append("title", "HELLLO");
data.append("message", "HELLO TEST Token");
data.append("token", "Enter your token");
data.append("projectname", "project name which you enter form submit");

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://fcm.papayacoders.com/api/send-token-notice");

xhr.send(data);


```

### Kotlin Code

```
val client = OkHttpClient()
val mediaType = "text/plain".toMediaType()
val body = MultipartBody.Builder().setType(MultipartBody.FORM)
  .addFormDataPart("title","HELLLO")
  .addFormDataPart("message","HELLO TEST Token")
  .addFormDataPart("token","Enter your token")
  .addFormDataPart("projectname","project name which you enter form submit")
  .build()
val request = Request.Builder()
  .url("https://fcm.papayacoders.com/api/send-token-notice")
  .post(body)
  .build()
val response = client.newCall(request).execute()
```


> Same process for /api/send-topic-notice only field topic you need to add your topic and send
## FCM Data/Notification Push Notification Integration

Bse url  - https://fcm.papayacoders.com/api/send-notice/{projectname}/{fcmtype}/{token}/{type}

in Url you need to add these parameter Mandatory
  - {projectname} replace this and add your Project id which you fill on fomr submission time
  - {fcmtype} replace this and add which type notice you want to send like : topic or token one of them same case
  - if you add fcmtype is token so {token} replace to your user fcm token
  - if you add fcm type is topic so {token} replace to your user fcm topic
  - {type} replace this to which type of notification you want send like Notification or Data

And last you need to send body data into Raw json 
{
  "click_action": "your_click_action_value",
  "title": "your_title_value",
  "body": "your_body_value",
  "image": "your_image_value"
}

You can add all key whih firebase allowed

after success ypu will this response
```
{"success":true,"data":{"name":"projects\/projectid\/messages\/0:1726816682076675%78d194c278d194c2"},"msg":"Success"}
```
