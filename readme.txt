if (!file.isEmpty()) {
		try {
			// 文件保存路径
			String path = request.getSession().getServletContext().getRealPath("");
			System.err.println(path);
			path = path.replaceAll("proxy_manage", "");  		//proxy_manage 为项目名称
			System.err.println(path);
			path = path.substring(0, path.length() - 1);
			System.out.println(path);
			File newFile = new File(path + "images/student/");  //为图片文件夹下的图片存放文件夹目录
			if (!newFile.exists())
				newFile.mkdirs();
			String name = file.getOriginalFilename();
			String wei = name.substring(name.lastIndexOf("."), name.length());
			String uuid = UUID.randomUUID().toString();
			String filePath = path + "images/student/" + uuid + wei;
			// 转存文件
			file.transferTo(new File(filePath));
			// // img路径
			// String imgUrl = ImagUtils.imgUrl();
			return "/student/" + uuid + wei;
		} catch (Exception e) {
			e.printStackTrace();
		}
