# baidu-push-api
Baidu push message JDK

# change
- support http proxy

# Gradle

`compile 'com.github.qiuxiaoj:baidu-push-api:3.0.1'`

# usage

```java

	String appKey = "appkey";
	String secretKey = "secretKey";
	String host = "api.push.baidu.com";
	boolean enableProxy = true;
	String proxyHost = "1.1.1.1";
	Integer proxyPort = "80";
	PushKeyPair keyPair = new PushKeyPair(appKey, secretKey);
	BaiduPushClient client = new BaiduPushClient(keyPair, host);
	if (enableProxy) {
		InetSocketAddress proxyServer = new InetSocketAddress(proxyHost, proxyPort);
		HttpConfigure httpConfigure = new HttpConfigure();
		httpConfigure.setEnableProxy(enableProxy);
		httpConfigure.setProxy(new Proxy(Type.HTTP, proxyServer));
		client.setHttpConfigure(httpConfigure);
	}
	client.setChannelLogHandler(new YunLogHandler() {
		@Override
		public void onHandle(YunLogEvent event) {
			logger.info("Baidu Push Event Log: {}", event.getMessage());
		}
	});
	
```