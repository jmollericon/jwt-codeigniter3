# JWT in CodeIgniter 3

## Step 1
- Download jwt_helper.php and copy this in application/helpers

## Step 2
- Add jwt_helper in config/autoload.php ($autoload['helper'])

## Step 3
- Implement the following function in a controller to generate the token

```
	public function token() {
		$jwt = new JWT();

		$JwtSecretKey = 'YourSecretKey';
		$data = array(
			'id' => 1,
			'email' => 'test@mail.com',
			'role' => 'admin'
		);

		$token = $jwt->encode($data, $JwtSecretKey, 'HS256');
		echo $token;
	}
```

## Step 4
- Implement the following function in a controller to decode the token

```
	public function decode_token() {
		$token = $this->uri->segment(3);

		$jwt = new JWT();

		$JwtSecretKey = 'YourSecretKey';

		$decoded_token = $jwt->decode($token, $JwtSecretKey, 'HS256');

		// std_object
		print_r($decoded_token);

		// json
		$tokenJSON = $jwt->jsonEncode($decoded_token);
		echo $tokenJSON;
	}
```
