# PR.github.io
<! DOCTYPE html >
< html  lang = " ru " >
	< голова >
		< title > three.js webgl - геометрические фигуры </ title >
		< meta  charset = " utf-8 " >
		< meta  name = " viewport " content = " width = device-width, user-scaleable = no, minimum-scale = 1.0, maximum-scale = 1.0 " >
		< link  type = " text / css " rel = " stylesheet " href = " https://threejs.org/examples/main.css " >
	</ голова >
	< тело >
		< div  id = " info " >
			Трехмерные фигуры
		</ div >

		< script  type = " module " >

			импортировать * как  ТРИ  из  https://threejs.org/build/three.module.js ;

			импортировать  {  OrbitControls  }  из  https://threejs.org/examples/jsm/controls/OrbitControls.js ' ;

			вар  камера ,  сцена ,  рендерер ;
			var  Controls ;
			var  ambientLight ,  light ;
			init ( ) ;
			animate ( ) ;

			function  init ( )  {

				var  container  =  document . createElement (  'div'  ) ;
				документ . тело . appendChild (  контейнер  ) ;

				// КАМЕРА
				камера  =  новые  ТРИ . PerspectiveCamera (  45 ,  окно . InnerWidth / window . InnerHeight ,  1 ,  8000  ) ;
				камера . положение . набор (  300 ,  700 ,  900  ) ;

				// ФАРЫ
				ambientLight  =  новые  ТРИ . AmbientLight (  0x333333  ) ; 	// 0,2

				свет  =  новые  ТРИ . DirectionalLight (  0xFFFFFF ,  1.0  ) ;
				свет . положение . набор (  1 ,  1 ,  1  ) ;				
				// направление задается в GUI

				// RENDERER
				renderer  =  новые  ТРИ . WebGLRenderer (  {  сглаживание : истина  }  ) ;
				рендерер . setPixelRatio (  окно . devicePixelRatio  ) ;
				рендерер . setSize (  окно . внутренняя ширина ,  окно . внутренняя высота  ) ;
				контейнер . appendChild (  рендерер . domElement  ) ;

				// СОБЫТИЯ
				окно . addEventListener (  'изменить размер' ,  onWindowResize ,  false  ) ;

				// КОНТРОЛЬ
				controls  =  new  OrbitControls (  камера ,  средство визуализации . domElement  ) ;
				контроль . addEventListener (  'изменить' ,  отобразить  ) ;
				//controls.rotateSpeed ​​= 1; 
				контроль . enableZoom  =  true ;  
				контроль . zoomSpeed  =  0,5 ;  

				контроль . minDistance  =  500 ;
				контроль . maxDistance  =  2500 ;
				
				контроль . enableDamping  =  true ;

				// сама сцена
				сцена  =  новые  ТРИ . Сцена ( ) ;
				сцена . background  =  new  ТРИ . Цвет (  0xD3D3D3  ) ;

				сцена . добавить (  ambientLight  ) ;
				сцена . добавить (  светлый  ) ;
			

				// объекты сцены

					var  geometry  =  новые  ТРИ . BoxGeometry (  200 ,  200 ,  150  ) ;
					var  material  =  new  ТРИ . MeshPhongMaterial (  {  цвет : 0xFF4500  }  ) ;
					var  Cube  =  новые  ТРИ . Сетка (  геометрия ,  материал  ) ;
					Куб . положение . установить (  0 ,  0 ,  0  ) ;
					//Cube.rotation.y = Math.PI / 6;
					//scene.add (Куб);

					var  geometry  =  новые  ТРИ . SphereGeometry ( 100 ,  50 ,  50 ) ; 
					var  material  =  new  ТРИ . MeshPhongMaterial (  {  цвет : 0xc41e3a  }  ) ;
					var  Sphere1  =  новые  ТРИ . Сетка (  геометрия ,  материал  ) ;
					Сфера1 . положение . установить (  300 ,  0 ,  0  ) ;
					//scene.add (Sphere1);	

					
					var  radiusTop  =  64 ;  var  radiusBottom  =  128 ;
					var  heigth  =  240 ;  var  сегментов  =  16 ;
					
					var  geometry  =  новые  ТРИ . CylinderGeometry ( 
						radiusTop ,  radiusBottom ,  heigth ,  сегменты  ) ;
						
					var  material  =  new  ТРИ . MeshPhongMaterial (  {  цвет : 0x177245  }  ) ;
					var  piramida  =  новые  ТРИ . Сетка (  геометрия ,  материал  ) ;
					пирамида . положение . установить (  0 ,  0 ,  0  ) ; 
					//piramida.rotation.x = -Math.PI / 2; 					
					
					//scene.add (пирамида);

					
				var  textureLoader  =  новый  ТРИ . TextureLoader ( ) ;
				var  texture  =  textureLoader . загрузка (  'img / kot.png'  ) ;
				var  material  =  new  ТРИ . MeshBasicMaterial (  {  карта : текстура  }  ) ;
	
					
					var  geometry  =  новые  ТРИ . BoxGeometry (  300 ,  300 ,  300  ) ;
					var  Cube  =  новые  ТРИ . Сетка (  геометрия ,  материал  ) ;
					Куб . положение . установить (  0 ,  0 ,  0  ) ;
					//Cube.rotation.y = Math.PI / 6;
					сцена . добавить (  Куб  ) ;				

			}

			// ОБРАБОТКА СОБЫТИЙ


			function  onWindowResize ( )  {

				камера . аспект  =  окно . внутренняя ширина / окно . innerHeight ;
				камера . updateProjectionMatrix ( ) ;

				рендерер . setSize (  окно . внутренняя ширина ,  окно . внутренняя высота  ) ;

			}

			//

			function  animate ( )  {

				requestAnimationFrame (  анимировать  ) ;
				контроль . update ( ) ;  //
				render ( ) ;

			}

			function  render ( )  {

				рендерер . рендер (  сцена ,  камера  ) ;

			}			


		</ скрипт >

	</ body >
</ html >
