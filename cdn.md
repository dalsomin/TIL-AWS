## CDN

[Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/) 같은 CDN(Content Delivery Network)을 사용하여 AWS Elemental MediaStore에 저장된 콘텐츠를 제공할 수 있습니다. CDN은 전역적으로 배포된 서버 세트로 비디오 등의 콘텐츠를 캐싱합니다. 사용자가 콘텐츠를 요청하면 CDN은 이 요청을 지연 시간이 가장 짧은 엣지 로케이션으로 라우팅합니다. 콘텐츠가 해당 엣지의 캐시에 이미 저장되어 있는 경우, CDN은 즉시 콘텐츠를 제공합니다.
엣지 로케이션에 콘텐츠가 없으면 CDN은 오리진(예: MediaStore 컨테이너)에서 콘텐츠를 가져와 사용자에게 배포합니다.
