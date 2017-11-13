# Laravel5.2-VertifyCode
## Laravel5.2结合第三方验证码类库实现验证码功能
### 第一步、把第三方类验证码放在源文件的resources目录下，再新建一个org目录，放在里面可以解压上面的压缩包
### 第二步、在控制器引入验证码类
```php
require_once 'resources\org\code\vcode.class.php';
```
### 第三步、编写生成验证码的方法，并创建对应生成验证码的路由
```php
public function code(){
        $vcode = new \Vcode;
        $vcode->doimg();
    }
```
```php
Route::get('admin/code','Admin\LoginController@code');
```
### 第四步、在前端接收
```html
<img src="{{url('admin/code')}}" alt="" onclick="this.src='{{url('admin/code')}}?'+Math.random()">
```
### 第五步、可以调用第三方验证码类中的get方法获取验证码的值，判断用户输入的是否一致
```php
public function getcode(){
        $vcode = new \Vcode;
        echo $vcode->get();
    }
```
```php
Route::get('admin/getcode','Admin\LoginController@getcode');
```
