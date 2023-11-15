# form-validation-from-aseaful-sir-


<?php 
	/**
	 * Student Data Form 
	 */
	if( isset($_POST['submit'])){
		// Form Value get 

		$name = $_POST['name'];
		$email = $_POST['email'];
		$cell = $_POST['cell'];
		$user =  $_POST['user'];

		


		//Check email
		if( isset($email)){
			$email_arra = explode('@', $email);
			$insta_mail = end($email_arra);
		}


		//Check number oparator 

		 $cell_start = substr( $cell, 0, 3);




		if ( empty($name)){
			$err['name'] = "<p style=\" color: red;\"> * Required</p>"; 
		}
		if ( empty($email)){
			$err['email'] = "<p style=\" color: red;\"> * Required</p>"; 
		}
		if ( empty($cell)){
			$err['cell'] = "<p style=\" color: red;\"> * Required</p>"; 
		}
		if ( empty($user)){
			$err['user'] = "<p style=\" color: red;\"> * Required</p>"; 
		}

		/**
		 * Form validation 
		 */

		if( empty($name) || empty($email) || empty($cell) || empty($user)){
			$msg = "<p class=\" alert alert-danger\">All feilds are required!!! <button class=\"close\" data-dismiss=\"alert\">&times;</button></p>";

		}else if( $insta_mail != 'albiak47.com'){
			$msg = "<p class=\" alert alert-info\">You should have a albiak47.com email to regiter!  <button class=\"close\" data-dismiss=\"alert\">&times;</button></p>";

		} else if( in_array($cell_start, ['017','013','016','018','015', '019','014']) == false){
			$msg = "<p class=\" alert alert-info\">Mobile number should be BD number<button class=\"close\" data-dismiss=\"alert\">&times;</button></p>";

		}
		else if(filter_var($email, FILTER_VALIDATE_EMAIL) == false) {
			$msg = "<p class=\" alert alert-warning\">Invalid email address! <button class=\"close\" data-dismiss=\"alert\">&times;</button></p>";
		}
		else{
			$msg = "<p class=\"alert alert-success\"> Data stable <button class=\"close\" data-dismiss=\"alert\">&times;</button></p>";
		}





	}
	
	
	
	?>
