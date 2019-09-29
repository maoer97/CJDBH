<template>
  <!-- 三维地图展示 -->
  <div class="box">
    <div id="cesiumContainer"></div>
  </div>
</template>

<script>
  // import Cesium from 'cesium/Cesium'
  // import 'cesium/Widgets/widgets.css'
  export default {
    name: 'App',
    mounted() {
      // this.$nextTick(()=>{
      //   var currentHost = window.location.host;
      //   var earth_base_url = "http://" + currentHost + "/";


      //   var  jichuImageUrl='';
      //   var  vectorImageUrl='';

      //   Cesium.BingMapsApi.defaultKey = 'AvzM4FgDkpuZwkwP9DPDUwq15NUTJxHNyyUHGSXiA9JwAtAinnlPS31PvwB3hcWh'; // For use in this application only. Do not reuse!
      //   Cesium.Ion.defaultAccessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJhNWIzMTYyZS1kMmQyLTRkOTAtYmRhZC0yZjZhOTE2YzZmYTEiLCJpZCI6MTI2NDksInNjb3BlcyI6WyJhc3IiLCJnYyJdLCJpYXQiOjE1NjE1NDE0ODh9.0jXPnp2IJ0RJ2gwvok4ybt0aIbekgiKRJbi-ehThGO4';



      //       var  imageryProvider = new Cesium.MapboxImageryProvider({
      //       mapId : 'mapbox.satellite'
      //       });

      //       var  TianDiTu_Laber = new Cesium.WebMapTileServiceImageryProvider({
      //           url:'http://t0.tianditu.gov.cn/cia_w/wmts',
      //           layer: "cia",
      //           style: "default",
      //           format: "tiles",
      //           tileMatrixSetID: "w",
      //           dimensions:{tk:'8cf3af25e445d634f1f8ba4572aebb41'},
      //           show: false
      //       });
      //       var wuhanimage = new Cesium.WebMapTileServiceImageryProvider({
      //           //url :'http://192.168.99.56:8080/geoserver/gwc/demo/hubei_data:hb_region?',
      //           url :'http://111.47.18.22:9626/geoserver/gwc/service/wmts',
      //           layer : 'hubei_data:wuhan_public_sat_18',
      //           style : '',
      //           tileMatrixSetID : 'EPSG:4326',
      //           maximumLevel : 18,
      //           format : 'image/png',
      //           tileMatrixLabels : ['EPSG:4326:0', 'EPSG:4326:1', 'EPSG:4326:2', 'EPSG:4326:3', 'EPSG:4326:4', 'EPSG:4326:5', 'EPSG:4326:6', 'EPSG:4326:7', 'EPSG:4326:8', 'EPSG:4326:9', 'EPSG:4326:10', 'EPSG:4326:11', 'EPSG:4326:12', 'EPSG:4326:13', 'EPSG:4326:14', 'EPSG:4326:15', 'EPSG:4326:16', 'EPSG:4326:17', 'EPSG:4326:18', 'EPSG:4326:19', 'EPSG:4326:20', 'EPSG:4326:21'],
      //           tilingScheme:new Cesium.GeographicTilingScheme(),
      //           enablePickFeatures:false,
      //           rectangle : Cesium.Rectangle.fromDegrees(113.69653880596161,29.9717116355896,115.07703959941864,31.363327503204346),
      //       });

      //   function SelectLayer(ImageryLayer){
      //       if(ImageryLayer == 'Bing') {
      //           /**
      //            * 加载全球影响Bing服务数据
      //            * @type {*}
      //            */
      //           imageryProvider = new Cesium.UrlTemplateImageryProvider({
      //           	url: "localhost:8080/Bings/tiles/{z}/{x}/{reverseY}.jpg",
      //               maximumLevel: 12 //根据数据调整，最大18
      //           });

      //       }
      //       else  if(ImageryLayer == 'geearth'){
      //           /**
      //            * 加载全球影响wmts服务数据
      //            * @type {*}
      //            */

      //           imageryProvider = new Cesium.WebMapTileServiceImageryProvider({
      //               //url: "http://192.168.1.235:3500/startlvlone/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=img&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //               //url: 'http://192.168.1.235:3500/startlvlone/wmts?',
      //           	url:jichuImageUrl,
      //               layer: 'geearth',
      //               style: "default",
      //               format: "image/jpeg",
      //               tileMatrixSetID: "ge",
      //               tilingScheme: new Cesium.GeographicTilingScheme(),
      //               tileMatrixLabels:['1','2','3','4','5','6','7','8','9','10','11','12','13','14','15','16','17','18','19','20','21','22','23','24']
      //               //MaximumLevel:18,

      //           });
      //       }
      //       else if(ImageryLayer == 'tdtBasicLayer'){
      //           /**
      //            * 加载全球天地图离线矢量服务
      //            */
      //           imageryProvider = new Cesium.WebMapTileServiceImageryProvider({
      //               //url: "http://192.168.1.235:5000/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=img&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //               url:vectorImageUrl,
      //           	layer: "tdtBasicLayer",
      //               style: "default",
      //               format: "image/jpg",
      //               tileMatrixSetID: "GoogleMapsCompatible",
      //               show: false
      //           });
      //       }
      //       else if(ImageryLayer == 'wms'){
      //           imageryProvider= new Cesium.WebMapTileServiceImageryProvider({
      //           url: "http://t0.tianditu.com/img_w/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=img&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //           //url: "http://t0.tianditu.com/vec_w/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=vec&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //           //主机图层
      //           //url: "http://t0.tianditu.com/cva_w/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=cva&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //           //url: "http://192.168.1.235:5000/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=img&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //           layer: "tdtBasicLayer",
      //           style: "default",
      //           format: "image/jpg",
      //           tileMatrixSetID: "GoogleMapsCompatible",
      //           show: false
      //       })
      //       }
      //       else if(ImageryLayer == 'wmsSL'){
      //           imageryProvider= new Cesium.WebMapTileServiceImageryProvider({
      //               url: "http://t0.tianditu.com/vec_w/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=vec&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //           //url: "http://t0.tianditu.com/vec_w/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=vec&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //           //主机图层
      //           //url: "http://t0.tianditu.com/cva_w/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=cva&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //           //url: "http://192.168.1.235:5000/wmts?service=wmts&request=GetTile&version=1.0.0&LAYER=img&tileMatrixSet=w&TileMatrix={TileMatrix}&TileRow={TileRow}&TileCol={TileCol}&style=default&format=tiles",
      //           layer: "tdtBasicLayer",
      //           style: "default",
      //           format: "image/jpg",
      //           tileMatrixSetID: "GoogleMapsCompatible",
      //           show: false
      //       })
      //       }
      //       else if(ImageryLayer == 'tianditu'){
      //           imageryProvider=  new Cesium.WebMapTileServiceImageryProvider({
      //               url: 'http://t0.tianditu.gov.cn/img_w/wmts',
      //               layer: "img",
      //               style: "default",
      //               format: "tiles",
      //               tileMatrixSetID: "w",
      //               dimensions:{tk:'8cf3af25e445d634f1f8ba4572aebb41'},
      //               show: false
      //           });
      //       }
      //       else if(ImageryLayer=="ArcGIS"){
      //           imageryProvider= new Cesium.ArcGisMapServerImageryProvider({
      //               url : 'https://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer'
      //           });
      //       }
      //       else if(ImageryLayer=="streetMap"){
      //           imageryProvider= new Cesium.createOpenStreetMapImageryProvider({
      //               url:  'https://a.tile.openstreetmap.org/',
      //           });
      //       }

      //       viewer.imageryLayers.remove(viewer.imageryLayers.get(0));
      //       viewer.imageryLayers.addImageryProvider(imageryProvider,0);
      //   }
      //   const viewer = new Cesium.Viewer('cesiumContainer',{
      //     animation: false,  //是否显示动画控件
      //     baseLayerPicker: false, //是否显示图层选择控件
      //     geocoder: false, //是否显示地名查找控件
      //     timeline: false, //是否显示时间线控件
      //     navigationHelpButton: false, //是否显示帮助信息控件
      //     selectionIndicator: false,
      //     navigationInstructionsInitiallyVisible: false,
      //     infoBox: false,  //是否显示点击要素之后显示的信息
      //     sceneModePicker : true,//是否显示3D/2D选择器
      //     vrButton:true,//双屏模式,默认不显示false
      //     imageryProvider:imageryProvider,
      //     terrainProvider : Cesium.createWorldTerrain(),
      //   })

      //   Cesium.Camera.DEFAULT_VIEW_RECTANGLE = Cesium.Rectangle.fromDegrees(60.00, 60.0, 160, 8.0);

      //   viewer.imageryLayers.addImageryProvider(Bing);
      //   // viewer.imageryLayers.addImageryProvider(TianDiTu_Laber);
      //   // viewer.imageryLayers.addImageryProvider(wuhanimage);

      //   viewer.extend(Cesium.viewerCesiumNavigationMixin, {});
      //   document.getElementsByClassName('cesium-widget-credits')[0].style.display = 'none';
      //   viewer.animation.container.style.visibility = 'hidden';
      //   viewer.timeline.container.style.visibility = 'hidden';
      //   document.getElementsByClassName('cesium-viewer-animationContainer')[0].style.display = 'none';
      //   viewer.scene.globe.enableLighting = false;
      //   /**
      //    *
      //    * @param x  经度位置
      //    * @param y  纬度位置
      //    * @param z  地面高程
      //    * @param name 标记点显示名称
      //    * @param srcimage 标记位置图片路劲
      //    */
      //   function addbillboard(x,y,z,name,srcimage) {
      //       var entity = viewer.entities.add({
      //           name :name,
      //           position : Cesium.Cartesian3.fromDegrees(x, y,z),
      //           // point : { //点
      //           //     pixelSize : 5,
      //           //     color : Cesium.Color.RED,
      //           //     outlineColor : Cesium.Color.WHITE,
      //           //     outlineWidth : 2
      //           // },
      //           billboard  : {
      //               scale: 1.3,  //原始大小的缩放比例
      //               image: srcimage,
      //               // horizontalOrigin: Cesium.HorizontalOrigin.CENTER,
      //               // verticalOrigin: Cesium.VerticalOrigin.BOTTOM, // default: CENTER
      //               // heightReference: Cesium.HeightReference.RELATIVE_TO_GROUND //CLAMP_TO_GROUND
      //           },
      //           label:{
      //               //文字标签
      //               text : name,
      //               font : '12pt monospace',
      //               fillColor: new Cesium.Color(0.6, 0.2, 1.0),
      //               outlineColor: Cesium.Color.BLACK,
      //               outlineWidth: 2,
      //               style :  Cesium.LabelStyle.FILL_AND_OUTLINE ,
      //               outlineWidth : 2,
      //               //translucencyByDistance: new Cesium.NearFarScalar(200, 1, 500, 0),
      //               verticalOrigin : Cesium.VerticalOrigin.BOTTOM, //垂直方向以底部来计算标签的位置
      //               pixelOffset : new Cesium.Cartesian2( 0, -20 )   //偏移量

      //           }
      //       })
      //       //viewer.flyTo(entity);
      //       //isflyTo(x,y,z);
      //   }
      //   //Cartesian 方式确定位置
      //   viewer.camera.flyTo({
      //       destination :  Cesium.Cartesian3.fromDegrees(107.29742,34.597944, 21348278.0), // 设置位置
      //       orientation: {
      //           heading : Cesium.Math.toRadians(0.0), // 方向
      //           pitch : Cesium.Math.toRadians(-90.0),// 倾斜角度
      //           roll : 0
      //       },
      //       duration:8, // 设置飞行持续时间，默认会根据距离来计算
      //       complete: function () {
      //           // 到达位置后执行的回调函数
      //           console.log('到达目的地');
      //       },
      //       cancle: function () {
      //           // 如果取消飞行则会调用此函数
      //           console.log('飞行取消')
      //       },
      //       pitchAdjustHeight: -90, // 如果摄像机飞越高于该值，则调整俯仰俯仰的俯仰角度，并将地球保持在视口中。
      //       maximumHeight:21348278, // 相机最大飞行高度
      //       flyOverLongitude: 100, // 如果到达目的地有2种方式，设置具体值后会强制选择方向飞过这个经度
      //   });
      //   var scene = viewer.scene;
      //   var px =104.09173200511712,py =34.66889079291384,pz =30;
      //   var handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //   function SetTitle() {
      //       handler.setInputAction(function(evt) {
      //           var scene = viewer.scene;
      //           //var attModel = scene.pick(evt.position).name;
      //           if (scene.mode !== Cesium.SceneMode.MORPHING) {
      //               var pickedObject = scene.pick(evt.position);
      //               //if (scene.pickPositionSupported && Cesium.defined(pickedObject) && pickedObject.node) {
      //               if (scene.pickPositionSupported && Cesium.defined(pickedObject) ){
      //                   var cartesian = viewer.scene.pickPosition(evt.position);
      //                   if (Cesium.defined(cartesian)) {
      //                       var cartographic = Cesium.Cartographic.fromCartesian(cartesian);
      //                       var lng = Cesium.Math.toDegrees(cartographic.longitude);
      //                       px = lng;
      //                       var lat = Cesium.Math.toDegrees(cartographic.latitude);
      //                       py = lat;
      //                       var height = cartographic.height;//模型高度
      //                       pz = height;
      //                       mapPosition={x:lng,y:lat,z:height};
      //                       var entitys = new addbillboard(px,py,pz,pickedObject.id.name);
      //                   }
      //               }
      //           }
      //       }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
      //   }
      //   function  addfly() {
      //       var Airentity = viewer.entities.add({
      //           model:{
      //               uri: earth_base_url + "modeldata/models/CesiumAir/Cesium_Air.gltf",
      //               minimumPixelSize:64
      //           },
      //           position:Cesium.Cartesian3.fromDegrees(-112.110693, 36.0994841, 1000.0)
      //       });
      //       viewer.trackedEntity = Airentity;
      //       return  Airentity;
      //   }
      //   function Addshp() {
      //       var ShapeLine = Cesium.GeoJsonDataSource.load(earth_base_url + 'modeldata/ChinaLine.topojson');
      //       ShapeLine.then(function (dataSource) {
      //           viewer.dataSources.add(dataSource);
      //           var shpentities = dataSource.entities.values;
      //           var ispolyline = shpentities.polyline;
      //           if(ispolyline)
      //           {
      //               shpentities.polyline.material = Cesium.ColorMaterialProperty.fromColor( Cesium.Color.BLUE);
      //           }
      //           //shpentities.polyline.material = Cesium.ColorMaterialProperty.fromColor(color);
      //       })
      //   }
      //   function isflyTo(x,y,z) {

      //       var toviewer = viewer.camera.flyTo({
      //           destination :  Cesium.Cartesian3.fromDegrees(x,y,z+1100000), // 设置位置

      //           orientation: {
      //               heading : Cesium.Math.toRadians(0.0), // 方向
      //               pitch : Cesium.Math.toRadians(-80.0),// 倾斜角度
      //               roll : 0
      //           },
      //       duration: 3
      //       });
      //   }

      //   Cesium.Math.setRandomNumberSeed(0);
      //   function addModel() {
      //       viewer.entities.removeAll();
      //       var struil = earth_base_url + "modeldata/models/CesiumMan/Cesium_Man.gltf";
      //       addSingleModel(viewer,12,struil,104.3938684795,46.5053912785,10,1);
      //   }
      //   function addModels() {
      //       viewer.entities.removeAll();//Data/SampleData/models/CesiumAir/Cesium_Air.gltf
      //       var struils = earth_base_url + "modeldata/models/CesiumAir/Cesium_Air.gltf";
      //       addSingleModel(viewer,12,struils,104.3938684795,44.5053912785,100,1);
      //   }
      //   /**
      //    * 添加单个模型
      //    * @param viewer
      //    * @param id
      //    * @param url
      //    * @param longitude
      //    * @param latitude
      //    * @param height
      //    * @param scale
      //    * @param isAnimation
      //    * @param isClampGround
      //    */
      //   function addSingleModel(viewer, id, url, longitude, latitude, height, scale, isAnimation, isClampGround) {
      //       var model = viewer.entities.add({
      //           id: id,
      //           position: Cesium.Cartesian3.fromDegrees(longitude, latitude, height),
      //           model: {
      //               uri: url,
      //               scale: scale,
      //               minimumPixelSize: 1,
      //               maximumScale: 20000,
      //               runAnimations: isAnimation,
      //               heightReference: isClampGround ? Cesium.HeightReference.CLAMP_TO_GROUND : Cesium.HeightReference.RELATIVE_TO_GROUND
      //           },
      //           description: "这是我的贴图<br/> <img src= '../Data/SampleData/models/CesiumAir/0_Cesium_Air.png' style='height:150px;width:150px;'/><br/>这是一个测试<br/><a href='http://www.baidu.com'>我是一个超链接<a/>"
      //       });
      //       viewer.trackedEntity = model;
      //   }
      //   /**
      //    * 关闭实体标注
      //    * @constructor
      //    */
      //   function ClearEntity() {
      //       viewer.entities.removeAll();
      //   }
      //   /**
      //    * 关闭加载的json数据源
      //    * @constructor
      //    */
      //   function ClearJson() {
      //       viewer.dataSources.removeAll();
      //   }

      //   /**
      //   *
      //   */
      //   //设置各种操作模式
      //   var scene = viewer.scene;
      //   var pinBuilder = new Cesium.PinBuilder();
      //   var vecLayer = null, roadLayer = null, electricLayers = null;
      //   var getEnumPropertyNames = function(obj) {
      //      var props = [];
      //      for (prop in obj) {
      //          props.push(prop + ': ' + obj[prop]);
      //      }
      //      return props;
      //   }
      //   var models = new Array();
      //   models[0] = { id: 'house1', name: 'house1', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.41, lat: 31.22, height: 0, pid: '4e027d42-f033-4bab-87f1-e34c8860b90e' };
      //   models[1] = { id: 'house2', name: 'house2', url: earth_base_url +  'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.42, lat: 31.21, height: 0, pid: '918dcfaa-4568-4468-ba03-e379deaa99b7' };
      //   models[2] = { id: 'house3', name: 'house3', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.43, lat: 31.20, height: 0, pid: '2071736b-0054-4041-ad34-34f2e7a975e5' };
      //   models[3] = { id: 'house4', name: 'house4', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltff', lon: 121.44, lat: 31.22, height: 0, pid: '4e027d42-f033-4bab-87f1-e34c8860b90e' };
      //   models[4] = { id: 'house5', name: 'house5', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.41, lat: 31.21, height: 0, pid: '918dcfaa-4568-4468-ba03-e379deaa99b7' };
      //   models[5] = { id: 'house6', name: 'house6', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.42, lat: 31.20, height: 0, pid: '2071736b-0054-4041-ad34-34f2e7a975e5' };
      //   models[6] = { id: 'house7', name: 'house7', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.43, lat: 31.22, height: 0, pid: '4e027d42-f033-4bab-87f1-e34c8860b90e' };
      //   models[7] = { id: 'house8', name: 'house8', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.44, lat: 31.21, height: 0, pid: '918dcfaa-4568-4468-ba03-e379deaa99b7' };
      //   models[8] = { id: 'house9', name: 'house9', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.45, lat: 31.20, height: 0, pid: '2071736b-0054-4041-ad34-34f2e7a975e5' };
      //   models[9] = { id: 'house10', name: 'house10', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.46, lat: 31.21, height: 0, pid: '918dcfaa-4568-4468-ba03-e379deaa99b7' };
      //   models[10] = { id: 'house11', name: 'house11', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.40, lat: 31.20, height: 0, pid: '4e027d42-f033-4bab-87f1-e34c8860b90e' };
      //   models[11] = { id: 'villa', name: 'villa', url: earth_base_url + 'modeldata/models/CesiumMan/Cesium_Man.gltf', lon: 121.45, lat: 31.22, height: 0, pid: '2071736b-0054-4041-ad34-34f2e7a975e5' };
      //   var loadedModels = [];
      //   var shapes = new Array();
      //   shapes[0] = { layer: '测试层', author: 'liu', date: '2017-06-18', ploy: [
      //      { name: 'A区', type: 'ploy', points: [] }
      //   ]};
      //   var tempPoints = [];
      //   var tempEntities = [];
      //   var tempPinEntities = [];
      //   var tempPinLon, tempPinLat;
      //   /**
      //   *
      //   * @param Xmodel // 绘制测量类型参数
      //   */
      //   function execute(Xmodel) {

      //      if (Xmodel=="") {
      //          clearEffects();
      //          setTips("");
      //      }
      //      else if (Xmodel =="addPin") {
      //          clearEffects();
      //          SetMode("addPin");
      //          setTips("首先在地图上点击需要加点的位置，然后在弹出框内选取颜色，设置提示文字和显示内容，点击保存");
      //      }
      //      else if ( Xmodel =="erase") {
      //          tempPoints = [];
      //          for (var i = 0; i < tempEntities.length; i++) {
      //              viewer.entities.remove(tempEntities[i]);
      //          }
      //          for (var i = 0; i < loadedModels.length; i++) {
      //              if (loadedModels[i].color == Cesium.Color.SPRINGGREEN) {
      //                  loadedModels[i].color = {red:1,green:1, blue:1, alpha:1};
      //              }
      //          }
      //          viewer.entities.removeAll();
      //          clearEffects();
      //          setTips("绘制的图形被清除，点选页面标记可以删除标记");
      //          SetMode("erase");
      //      }
      //      else if (Xmodel=="drawLine") {
      //          clearEffects();
      //          SetMode("drawLine");
      //          setTips("在地图上分别点击，即可绘制多个线段，点右键结束绘制");
      //      }
      //      else if (Xmodel =="drawCircle") {
      //          clearEffects();
      //          SetMode("drawCircle");
      //          setTips("第一次点击绘制圆心，第二次点击根据和圆心的位置绘制半径");
      //      }
      //      else if (Xmodel == "drawSquare") {
      //          clearEffects();
      //          SetMode("drawSquare");
      //          setTips("第一、二次点击绘制长方形的一个边，再次点击根据点和边的距离绘制方形");
      //      }
      //      else if (Xmodel == "drawPloy") {
      //          clearEffects();
      //          SetMode("drawPloy");
      //          setTips("如果需要绘制多边形，在地图上使用左键逐个点选地点，右击闭合多边形");
      //      }
      //      else if (Xmodel =="pickBuilding") {
      //          clearEffects();
      //          SetMode("pickBuilding");
      //          setTips("点选建筑查看详细的三维模型");
      //      }
      //   }
      //   /**
      //   * 添加数组模型
      //   */
      //   function addArrayModel() {
      //      LoadModel();
      //   };
      //   /**
      //   * 影藏模型数据
      //   * @constructor
      //   */
      //   function HideModels() {
      //      HideModel();
      //   };
      //   var handler = null;

      //   function LoadModel() {
      //      for (var i = 0; i < models.length; i++) {
      //          var hasLoaded = false;
      //          for (var j = 0; j < loadedModels.length; j ++) {
      //              if (models[i].id == loadedModels[j].id) {
      //                  hasLoaded = true;
      //              }
      //          }
      //          if (!hasLoaded) {
      //              var modelMatrix = Cesium.Transforms.eastNorthUpToFixedFrame(
      //                  Cesium.Cartesian3.fromDegrees(models[i].lon, models[i].lat, models[i].height));

      //              var model = scene.primitives.add(
      //                  Cesium.Model.fromGltf({
      //                      url: models[i].url,
      //                      modelMatrix: modelMatrix,
      //                      scale: 20.0,
      //                      name: models[i].name,
      //                      id: models[i].id
      //                  }));
      //              loadedModels.push(model);
      //          }
      //      }
      //      // var cartesian = viewer.camera.pickEllipsoid(loadedModels[0].modelMatrix, scene.globe.ellipsoid);
      //      // alert(getEnumPropertyNames(cartesian).join('\r'));

      //   }
      //   function HideModel() {
      //      for (var i = 0; i < loadedModels.length; i++) {
      //          scene.primitives.remove(loadedModels[i]);
      //      }
      //      loadedModels = [];
      //   }
      //   function setTips(message, close) {
      //      if ("" == message) {
      //          $("#message").fadeOut();
      //      } else {
      //          if (close != undefined && close == true) {
      //              $("#message").html(message).fadeOut();
      //          } else {
      //              $("#message").html(message).fadeIn();
      //          }
      //      }
      //   }
      //   function clearEffects() {
      //      if (handler != null) {
      //          handler.destroy();
      //      }
      //   }
      //   //设置各种操作模式
      //   function SetMode(mode) {
      //      if (mode == "drawPloy")
      //      {
      //          tempPoints = [];
      //          handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //          handler.setInputAction(function (click) {
      //              var cartesian = viewer.camera.pickEllipsoid(click.position, scene.globe.ellipsoid);
      //              if (cartesian) {
      //                  var cartographic = Cesium.Cartographic.fromCartesian(cartesian);
      //                  var longitudeString = Cesium.Math.toDegrees(cartographic.longitude);
      //                  var latitudeString = Cesium.Math.toDegrees(cartographic.latitude);
      //                  tempPoints.push({ lon: longitudeString, lat: latitudeString });
      //                  var tempLength = tempPoints.length;
      //                  drawPoint(tempPoints[tempPoints.length-1]);
      //                  if (tempLength > 1) {
      //                      drawLine(tempPoints[tempPoints.length - 2], tempPoints[tempPoints.length - 1], true);
      //                  }
      //              }
      //          }, Cesium.ScreenSpaceEventType.LEFT_CLICK);

      //          handler.setInputAction(function (click) {
      //              var cartesian = viewer.camera.pickEllipsoid(click.position, scene.globe.ellipsoid);
      //              if (cartesian) {
      //                  var tempLength = tempPoints.length;
      //                  if (tempLength < 3) {
      //                      alert('请选择3个以上的点再执行闭合操作命令');
      //                  } else {
      //                      drawLine(tempPoints[0], tempPoints[tempPoints.length - 1], true);
      //                      drawPoly(tempPoints);
      //                      highLightAssetsInArea(tempPoints);
      //                      //alert('多边形面积' + SphericalPolygonAreaMeters(tempPoints) + '平方米');
      //                      var  strPloyArea =  '多边形面积' + SphericalPolygonAreaMeters(tempPoints) + '平方米';
      //                      OffsetByDistance(tempPoints[0].lon,tempPoints[0].lat,10,strPloyArea);
      //                      tempPoints = [];
      //                  }

      //              }
      //         // }, Cesium.ScreenSpaceEventType.RIGHT_CLICK );
      //          }, Cesium.ScreenSpaceEventType.MOUSE_MOVE );
      //      }
      //      else if (mode == "pickBuilding")
      //      {
      //          handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //          handler.setInputAction(function(click) {
      //              var pick = scene.pick(click.position);
      //              if (Cesium.defined(pick) && Cesium.defined(pick.node) && Cesium.defined(pick.mesh)) {
      //                  for (var i = 0; i < models.length; i ++) {
      //                      if (models[i].id == pick.node._model.id) {
      //                          var modelName = models[i].name;
      //                          var modelId = models[i].id;
      //                          var modelBimId = models[i].pid;
      //                          highLigthModel(modelId);
      //                          viewer.camera.flyTo({
      //                              destination: Cesium.Cartesian3.fromDegrees(models[i].lon, parseFloat(models[i].lat) - 0.01, 2000.0),
      //                              orientation: {
      //                                  direction: new Cesium.Cartesian3(0.5437275903005284, -0.8386290220423197, -0.03258329225728158),
      //                                  up: new Cesium.Cartesian3(0.05520718287689969, -0.00299987805272847, 0.9984704140286108)
      //                              },
      //                              complete: function() {
      //                                  if (confirm("你选择的是" + modelName + "，是否查看详细模型？")) {
      //                                      LoadBim(modelBimId);
      //                                  }
      //                                  unHighLightModel(modelId);
      //                              },
      //                          });
      //                      }
      //                  }
      //              }
      //          }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
      //      }
      //      else if ( mode=="addPin")
      //      {
      //          handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //          handler.setInputAction(function (click) {
      //              var cartesian = viewer.camera.pickEllipsoid(click.position, scene.globe.ellipsoid);
      //              if (cartesian) {
      //                  var cartographic = Cesium.Cartographic.fromCartesian(cartesian);
      //                  tempPinLon = Cesium.Math.toDegrees(cartographic.longitude);
      //                  tempPinLat = Cesium.Math.toDegrees(cartographic.latitude);
      //                  $('#addPinModal').modal('show');
      //              }
      //          }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
      //      }
      //      else if (mode == "erase" )
      //      {
      //          handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //          handler.setInputAction(function (click) {
      //              var pick = scene.pick(click.position);
      //              if (Cesium.defined(pick) && Cesium.defined(pick.id) && Cesium.defined(pick.id._id)) {
      //                  for (var i = 0; i < models.length; i++) {
      //                      if ( pick.id != undefined && tempPinEntities[i].id == pick.id._id) {
      //                          removePoint(tempPinEntities[i]);
      //                          tempPinEntities.splice(i, 1);
      //                      }
      //                  }
      //              }
      //          }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
      //      }
      //      else if (mode == "drawLine" )
      //      {
      //          tempPoints = [];
      //          handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //          handler.setInputAction(function (click) {
      //              var cartesian = viewer.camera.pickEllipsoid(click.position, scene.globe.ellipsoid);
      //              if (cartesian) {
      //                  var cartographic = Cesium.Cartographic.fromCartesian(cartesian);
      //                  var longitudeString = Cesium.Math.toDegrees(cartographic.longitude);
      //                  var latitudeString = Cesium.Math.toDegrees(cartographic.latitude);
      //                  tempPoints.push({ lon: longitudeString, lat: latitudeString });
      //                  var tempLength = tempPoints.length;
      //                  drawPoint(tempPoints[tempPoints.length - 1]);
      //                  if (tempLength > 1) {
      //                      drawLine(tempPoints[tempPoints.length - 2], tempPoints[tempPoints.length - 1], true);
      //                  }
      //              }
      //          }, Cesium.ScreenSpaceEventType.LEFT_CLICK);

      //          handler.setInputAction(function (click) {
      //              tempPoints = [];
      //          }, Cesium.ScreenSpaceEventType.RIGHT_CLICK );
      //      }
      //      else if ( mode =="drawCircle" )
      //      {
      //          tempPoints = [];
      //          handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //          handler.setInputAction(function (click) {
      //              var cartesian = viewer.camera.pickEllipsoid(click.position, scene.globe.ellipsoid);
      //              if (cartesian) {
      //                  var cartographic = Cesium.Cartographic.fromCartesian(cartesian);
      //                  var longitudeString = Cesium.Math.toDegrees(cartographic.longitude);
      //                  var latitudeString = Cesium.Math.toDegrees(cartographic.latitude);
      //                  tempPoints.push({ lon: longitudeString, lat: latitudeString });
      //                  var tempLength = tempPoints.length;
      //                  if (tempLength == 1) {
      //                      drawPoint(tempPoints[0]);
      //                  }
      //                  else if (tempLength == 2) {
      //                      drawPoint(tempPoints[1]);
      //                      drawLine(tempPoints[0], tempPoints[1], true);
      //                      //算两点间距离
      //                      var distance = getFlatternDistance(tempPoints[0].lat, tempPoints[0].lon, tempPoints[1].lat, tempPoints[1].lon);

      //                      var entity = viewer.entities.add({position: Cesium.Cartesian3.fromDegrees(tempPoints[0].lon, tempPoints[0].lat),
      //                              ellipse: {
      //                                  semiMinorAxis: distance,
      //                                  semiMajorAxis: distance,
      //                                  height: 0,
      //                                  material: Cesium.Color.fromRandom({ alpha: 0.8 })
      //                              }
      //                          });
      //                      tempEntities.push(entity);

      //                      //高亮圈内模型
      //                      for (var i = 0; i < loadedModels.length; i++) {
      //                          for (var j = 0; j < models.length; j++) {
      //                              if (loadedModels[i].id == models[j].id && getFlatternDistance(models[j].lat, models[j].lon, tempPoints[0].lat, tempPoints[0].lon) <= distance) {
      //                                  loadedModels[i].color = Cesium.Color.SPRINGGREEN;
      //                              }
      //                          }
      //                      }

      //                      var PrintArea = "圆面积是 " + Math.PI * distance * distance + "平方米";
      //                      //面积
      //                      ////setTimeout(function () { alert("面积是 " + Math.PI * distance * distance + "平方米") },500);
      //                      setTimeout(OffsetByDistance(tempPoints[0].lon,tempPoints[0].lat,10,PrintArea));

      //                      tempPoints = [];
      //                  }
      //              }
      //          }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
      //      }
      //      else if (mode =="drawSquare" ) {
      //          tempPoints = [];
      //          handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //          handler.setInputAction(function (click) {
      //              var cartesian = viewer.camera.pickEllipsoid(click.position, scene.globe.ellipsoid);
      //              if (cartesian) {
      //                  var cartographic = Cesium.Cartographic.fromCartesian(cartesian);
      //                  var longitudeString = Cesium.Math.toDegrees(cartographic.longitude);
      //                  var latitudeString = Cesium.Math.toDegrees(cartographic.latitude);
      //                  tempPoints.push({ lon: longitudeString, lat: latitudeString });
      //                  var tempLength = tempPoints.length;
      //                  if (tempLength == 1) {
      //                      drawPoint(tempPoints[0]);
      //                  }
      //                  else if (tempLength == 2) {
      //                      //算两点间距离
      //                      var distance = getFlatternDistance(tempPoints[0].lat, tempPoints[0].lon, tempPoints[1].lat, tempPoints[1].lon);

      //                      var entity =
      //                          viewer.
      //                          entities.add({
      //                              position: Cesium.Cartesian3.fromDegrees(tempPoints[0].lon, tempPoints[0].lat),
      //                              ellipse: {
      //                                  semiMinorAxis: distance,
      //                                  semiMajorAxis: distance,
      //                                  height: 0,
      //                                  material: Cesium.Color.fromRandom({ alpha: 0.8 })
      //                              }
      //                          });
      //                      tempEntities.push(entity);

      //                      //高亮圈内模型
      //                      for (var i = 0; i < loadedModels.length; i++) {
      //                          for (var j = 0; j < models.length; j++) {
      //                              if (loadedModels[i].id == models[j].id && getFlatternDistance(models[j].lat, models[j].lon, tempPoints[0].lat, tempPoints[0].lon) <= distance) {
      //                                  loadedModels[i].color = Cesium.Color.SPRINGGREEN;
      //                              }
      //                          }
      //                      }

      //                      tempPoints = [];
      //                  }
      //              }
      //          }, Cesium.ScreenSpaceEventType.LEFT_CLICK);

      //      }
      //   }



      //   /**
      //    * 面积测量广告牌显示样式
      //    * @param longitude 经度
      //    * @param latitude 纬度
      //    * @param height 刚度
      //    * @param text 文本内容
      //    */
      //   function OffsetByDistance(longitude,latitude,height,text ) {
      //       //Sandcastle.declare(offsetByDistance);
      //       var image = new Image();
      //       image.onload = function() {
      //           viewer.entities.add({
      //               position : Cesium.Cartesian3.fromDegrees(longitude, latitude),
      //               billboard : {
      //                   position : Cesium.Cartesian3.fromDegrees(longitude, latitude),
      //                   scaleByDistance : new Cesium.NearFarScalar(1.5e2, 1.0, 1.5e7, 0.1),
      //                   image : image
      //               },
      //               point : { //点
      //                   pixelSize : 5,
      //                   color : Cesium.Color.RED,
      //                   outlineColor : Cesium.Color.WHITE,
      //                   outlineWidth : 2
      //               },
      //               label : {
      //                   text : text,
      //                   font : '17px sans-serif',
      //                   fillColor: new Cesium.Color(0.6, 0.9, 1.0),
      //                   outlineColor: Cesium.Color.BLACK,
      //                   outlineWidth: 3,
      //                   showBackground : true,
      //                   horizontalOrigin : Cesium.HorizontalOrigin.CENTER,
      //                   pixelOffset : new Cesium.Cartesian2(0.0, -image.height),
      //                   pixelOffsetScaleByDistance : new Cesium.NearFarScalar(1.5e2, 3.0, 1.5e7, 0.5)
      //               }
      //           });
      //       };
      //       image.src = "/rocket/static/images/point.png";
      //   }



      //   function drawPoint(point) {
      //      var entity =
      //          viewer.entities.add({
      //              position: Cesium.Cartesian3.fromDegrees(point.lon, point.lat),
      //              point: {
      //                  pixelSize: 10,
      //                  color: Cesium.Color.CHARTREUSE
      //              }
      //          });
      //      tempEntities.push(entity);
      //   }

      //   function removePoint(entity) {
      //      viewer.entities.remove(entity);
      //   }

      //   function drawLine(point1, point2, showDistance) {
      //      var entity =
      //          viewer.entities.add({
      //              polyline: {
      //                  positions: [Cesium.Cartesian3.fromDegrees(point1.lon, point1.lat), Cesium.Cartesian3.fromDegrees(point2.lon, point2.lat)],
      //                  width: 10.0,
      //                  material: new Cesium.PolylineGlowMaterialProperty({
      //                      color: Cesium.Color.CHARTREUSE.withAlpha(.5)
      //                  })
      //              }
      //          });
      //      tempEntities.push(entity);
      //      if (showDistance) {
      //          var w = Math.abs(point1.lon - point2.lon);
      //          var h = Math.abs(point1.lat - point2.lat);
      //          var offsetV = w >= h ? 0.0005 : 0;
      //          var offsetH = w < h ? 0.001 : 0;
      //          var distance = getFlatternDistance(point1.lat, point1.lon, point2.lat, point2.lon);
      //          entity =
      //              viewer.entities.add({
      //                  position: Cesium.Cartesian3.fromDegrees(((point1.lon + point2.lon) / 2) + offsetH,
      //                      ((point1.lat + point2.lat) / 2) + offsetV),
      //                  label: {
      //                      text: distance.toFixed(1) + 'm',
      //                      font: '22px Helvetica',
      //                      fillColor: Cesium.Color.WHITE
      //                  }
      //              });
      //          tempEntities.push(entity);
      //      }
      //   }

      //   function drawPoly(points) {
      //      var pArray = [];
      //      for (var i = 0; i < points.length; i ++) {
      //          pArray.push(points[i].lon);
      //          pArray.push(points[i].lat);
      //      }
      //      var entity =
      //          viewer.entities.add({
      //              polygon: {
      //                  hierarchy: new Cesium.PolygonHierarchy(Cesium.Cartesian3.fromDegreesArray(pArray)),
      //                  material: Cesium.Color.CHARTREUSE.withAlpha(.5)
      //              }
      //          });
      //      tempEntities.push(entity);
      //   }

      //   function getColor(colorName, alpha) {
      //      var color = Cesium.Color[colorName.toUpperCase()];
      //      return Cesium.Color.fromAlpha(color, parseFloat(alpha));
      //   }

      //   //判断点是否在多边形内
      //   function PointInPoly(point, polyPoints) {
      //      for (var c = false, i = -1, l = polyPoints.length, j = l - 1; ++i < l; j = i)
      //          ((polyPoints[i].lat <= point.lat && point.lat < polyPoints[j].lat) || (polyPoints[j].lat <= point.lat && point.lat < polyPoints[i].lat))
      //          && (point.lon < (polyPoints[j].lon - polyPoints[i].lon) * (point.lat - polyPoints[i].lat) / (polyPoints[j].lat - polyPoints[i].lat) + polyPoints[i].lon)
      //          && (c = !c);
      //      return c;
      //   }

      //   //选区内模型高亮
      //   function highLightAssetsInArea(points) {

      //      for (var i = 0; i < loadedModels.length; i++) {
      //          for (var j = 0; j < models.length; j ++) {
      //              if (loadedModels[i].id == models[j].id && PointInPoly(models[j], points)) {
      //                  loadedModels[i].color = Cesium.Color.SPRINGGREEN;
      //              }
      //          }
      //      }
      //   }

      //   //高亮模型
      //   function highLigthModel(modelId) {
      //      for (var i = 0; i < loadedModels.length; i ++) {
      //          if (loadedModels[i].id == modelId) {
      //              loadedModels[i].color = Cesium.Color.SPRINGGREEN;
      //          }
      //      }
      //   }

      //   //取消高亮模型
      //   function unHighLightModel(modelId) {
      //      for (var i = 0; i < loadedModels.length; i++) {
      //          if (loadedModels[i].id == modelId) {
      //              loadedModels[i].color = {
      //                  red: 1,
      //                  green: 1,
      //                  blue: 1,
      //                  alpha: 1
      //              };
      //          }
      //      }
      //   }

      //   //定位
      //   function goLocation() {
      //      $('#flyToModal').modal('hide');
      //      $('#flyToModal').on('hidden.bs.modal', function(e) {
      //          viewer.camera.flyTo({
      //              destination: Cesium.Cartesian3.fromDegrees($("#jumpLon").val(), $("#jumpLat").val(), 1000.0)
      //          });
      //      });
      //   }

      //   //加点
      //   function addPin() {
      //      $('#addPinModal').modal('hide');
      //      var pin = viewer.entities.add({
      //          name: $("#pinContent").val(),
      //          position: Cesium.Cartesian3.fromDegrees(tempPinLon, tempPinLat),
      //          billboard: {
      //              image: $("#pinLabel").val() == "" ? pinBuilder.fromColor(Cesium.Color[$("#pinColor").val().toUpperCase()], 48).toDataURL() :
      //                  pinBuilder.fromText($("#pinLabel").val(), Cesium.Color[$("#pinColor").val().toUpperCase()], 64).toDataURL(),
      //              verticalOrigin: Cesium.VerticalOrigin.BOTTOM
      //          }
      //      });
      //      tempPinEntities.push(pin);
      //      $("#pinLabel").val("");
      //      $("#pinContent").val("");
      //   }

      //   //计算两点间距离
      //   function getFlatternDistance(lat1, lng1, lat2, lng2) {
      //      var EARTH_RADIUS = 6378137.0;    //单位M
      //      var PI = Math.PI;

      //      function getRad(d) {
      //          return d * PI / 180.0;
      //      }
      //      var f = getRad((lat1 + lat2) / 2);
      //      var g = getRad((lat1 - lat2) / 2);
      //      var l = getRad((lng1 - lng2) / 2);

      //      var sg = Math.sin(g);
      //      var sl = Math.sin(l);
      //      var sf = Math.sin(f);

      //      var s, c, w, r, d, h1, h2;
      //      var a = EARTH_RADIUS;
      //      var fl = 1 / 298.257;

      //      sg = sg * sg;
      //      sl = sl * sl;
      //      sf = sf * sf;

      //      s = sg * (1 - sl) + (1 - sf) * sl;
      //      c = (1 - sg) * (1 - sl) + sf * sl;

      //      w = Math.atan(Math.sqrt(s / c));
      //      r = Math.sqrt(s * c) / w;
      //      d = 2 * w * a;
      //      h1 = (3 * r - 1) / 2 / c;
      //      h2 = (3 * r + 1) / 2 / s;

      //      return d * (1 + fl * (h1 * sf * (1 - sg) - h2 * (1 - sf) * sg));
      //   }

      //   //计算多边形面积
      //   var earthRadiusMeters = 6371000.0;
      //   var metersPerDegree = 2.0 * Math.PI * earthRadiusMeters / 360.0;
      //   var radiansPerDegree = Math.PI / 180.0;
      //   var degreesPerRadian = 180.0 / Math.PI;
      //   var pointArr;
      //   function SphericalPolygonAreaMeters(points) {
      //      var totalAngle = 0;
      //      for (var i = 0; i < points.length; i++) {
      //          var j = (i + 1) % points.length;
      //          var k = (i + 2) % points.length;
      //          totalAngle += Angle(points[i], points[j], points[k]);
      //      }
      //      var planarTotalAngle = (points.length - 2) * 180.0;
      //      var sphericalExcess = totalAngle - planarTotalAngle;
      //      if (sphericalExcess > 420.0) {
      //          totalAngle = points.length * 360.0 - totalAngle;
      //          sphericalExcess = totalAngle - planarTotalAngle;
      //      } else if (sphericalExcess > 300.0 && sphericalExcess < 420.0) {
      //          sphericalExcess = Math.abs(360.0 - sphericalExcess);
      //      }
      //      return sphericalExcess * radiansPerDegree * earthRadiusMeters * earthRadiusMeters;
      //   }

      //   /*角度*/
      //   function Angle(p1, p2, p3) {
      //      var bearing21 = Bearing(p2, p1);
      //      var bearing23 = Bearing(p2, p3);
      //      var angle = bearing21 - bearing23;
      //      if (angle < 0) {
      //          angle += 360;
      //      }
      //      return angle;
      //   }
      //   /*方向*/
      //   function Bearing(from, to) {
      //      var lat1 = from.lat * radiansPerDegree;
      //      var lon1 = from.lon * radiansPerDegree;
      //      var lat2 = to.lat * radiansPerDegree;
      //      var lon2 = to.lon * radiansPerDegree;
      //      var angle = -Math.atan2(Math.sin(lon1 - lon2) * Math.cos(lat2), Math.cos(lat1) * Math.sin(lat2) - Math.sin(lat1) * Math.cos(lat2) * Math.cos(lon1 - lon2));
      //      if (angle < 0) {
      //          angle += Math.PI * 2.0;
      //      }
      //      angle = angle * degreesPerRadian;
      //      return angle;
      //   }

      //   function LoadBim(projId) {
      //      //加载模型
      //      $('#myTabs li:eq(1) a').tab('show');

      //   }


      //   /**
      //   * 交互式绘制方法工具栏
      //   *
      //   */

      //   var drawHelper = new DrawHelper(viewer);
      //   var toolbar;
      //   function drawTool() {

      //      var scene = viewer.scene;
      //      var toolBarDiv = document.getElementById("toolbar");
      //      if (toolBarDiv.innerHTML == null || toolBarDiv.innerHTML == '') {
      //   	   toolbar = drawHelper.addToolbar(document.getElementById("toolbar"), {
      //   	       buttons: ['marker', 'polyline', 'polygon', 'circle', 'extent']});
      //   	   toolBarDiv.style.display = 'block';
      //      } else {
      //   	   toolBarDiv.style.display = 'block';
      //      }

      //      toolbar.addListener('markerCreated', function(event) {
      //          loggingMessage('Marker created at ' + event.position.toString());
      //          var b = new Cesium.BillboardCollection();
      //          scene.primitives.add(b);
      //          var billboard = b.add({
      //              show: true,
      //              position: event.position,
      //              pixelOffset: new Cesium.Cartesian2(0,0),
      //              eyeOffset: new Cesium.Cartesian3(0.0,0.0,0.0),
      //              horizontalOrigin: Cesium.HorizontalOrigin.CENTER,
      //              verticalOrigin: Cesium.VerticalOrigin.CENTER,
      //              scale: 1.0,
      //              image: '/rocket/static/images/mark.png',
      //              color: new Cesium.Color(1.0,1.0,1.0,1.0)
      //          });
      //          billboard.setEditable()
      //      });
      //      toolbar.addListener('polylineCreated', function(event) {
      //          loggingMessage('绘制线 ' + event.positions.length + ' 点');
      //          var polyline = new DrawHelper.PolylinePrimitive({
      //              positions: event.positions,
      //              width: 5,
      //              geodesic: true
      //          });
      //          scene.primitives.add(polyline);
      //          polyline.setEditable();
      //          polyline.addListener('onEdited', function(event) {
      //              loggingMessage('Polyline edited, ' + event.positions.length + ' points')
      //          })
      //      });
      //      toolbar.addListener('polygonCreated', function(event) {
      //          loggingMessage('Polygon created with ' + event.positions.length + ' points');
      //          var polygon = new DrawHelper.PolygonPrimitive({
      //              positions: event.positions,
      //              material: Cesium.Material.fromType('Checkerboard')
      //          });
      //          scene.primitives.add(polygon);
      //          polygon.setEditable();
      //          polygon.addListener('onEdited', function(event) {
      //              loggingMessage('Polygon edited, ' + event.positions.length + ' points')
      //          })
      //      });
      //      toolbar.addListener('circleCreated', function(event) {
      //          loggingMessage('Circle created: center is ' + event.center.toString() + ' and radius is ' + event.radius.toFixed(1) + ' meters');
      //          var circle = new DrawHelper.CirclePrimitive({
      //              center: event.center,
      //              radius: event.radius,
      //              material: Cesium.Material.fromType(Cesium.Material.RimLightingType)
      //          });
      //          scene.primitives.add(circle);
      //          circle.setEditable();
      //          circle.addListener('onEdited', function(event) {
      //              loggingMessage('Circle edited: radius is ' + event.radius.toFixed(1) + ' meters')
      //          })
      //      });
      //      toolbar.addListener('extentCreated', function(event) {
      //          var extent = event.extent;
      //          loggingMessage('Extent created (N: ' + extent.north.toFixed(3) + ', E: ' + extent.east.toFixed(3) + ', S: ' + extent.south.toFixed(3) + ', W: ' + extent.west.toFixed(3) + ')');
      //          var extentPrimitive = new DrawHelper.ExtentPrimitive({
      //              extent: extent,
      //              material: Cesium.Material.fromType(Cesium.Material.StripeType)
      //          });
      //          scene.primitives.add(extentPrimitive);
      //          extentPrimitive.setEditable();
      //          extentPrimitive.addListener('onEdited', function(event) {
      //              loggingMessage('Extent edited: extent is (N: ' + event.extent.north.toFixed(3) + ', E: ' + event.extent.east.toFixed(3) + ', S: ' + event.extent.south.toFixed(3) + ', W: ' + event.extent.west.toFixed(3) + ')')
      //          })
      //      });
      //      var loggings = document.getElementById('logging');

      //      function loggingMessage(message) {
      //          //loggings.innerHTML = message
      //      }
      //   }

      //   /**
      //   *  获取当前鼠标的经度、纬度、高度
      //   */
      //   function getPosition() {
      //      //得到当前三维场景
      //      var scene = viewer.scene;
      //      //得到当前三维场景的椭球体
      //      var ellipsoid = scene.globe.ellipsoid;
      //      var entity = viewer.entities.add({
      //          label : {
      //              show : false
      //          }
      //      });
      //      var longitudeString = null;
      //      var latitudeString = null;
      //      var height = null;
      //      var cartesian = null;
      //      // 定义当前场景的画布元素的事件处理
      //      var handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
      //      //设置鼠标移动事件的处理函数，这里负责监听x,y坐标值变化
      //      handler.setInputAction(function(movement) {
      //          //通过指定的椭球或者地图对应的坐标系，将鼠标的二维坐标转换为对应椭球体三维坐标
      //          cartesian = viewer.camera.pickEllipsoid(movement.endPosition, ellipsoid);
      //          if (cartesian) {
      //              //将笛卡尔坐标转换为地理坐标
      //              var cartographic = ellipsoid.cartesianToCartographic(cartesian);
      //              //将弧度转为度的十进制度表示
      //              longitudeString = Cesium.Math.toDegrees(cartographic.longitude);
      //              latitudeString = Cesium.Math.toDegrees(cartographic.latitude);
      //              //获取相机高度
      //              height = Math.ceil(viewer.camera.positionCartographic.height);
      //              entity.position = cartesian;
      //              document.getElementById("coordinate_location").innerHTML = "经度:" + longitudeString + "°，纬度:" + latitudeString  + "°";
      //              document.getElementById("coordinate_cameraheight").innerHTML = "视角海拔高度: " + height+ "米";
      //              //entity.label.show = true;
      //              //entity.label.text = '(' + longitudeString + ', ' + latitudeString + "," + height + ')' ;
      //          }else {
      //              entity.label.show = false;
      //          }
      //      }, Cesium.ScreenSpaceEventType.MOUSE_MOVE);

      //      //设置鼠标滚动事件的处理函数，这里负责监听高度值变化
      //      handler.setInputAction(function(wheelment) {
      //          height = Math.ceil(viewer.camera.positionCartographic.height);
      //          entity.position = cartesian;
      //          //entity.label.show = true;
      //          //entity.label.text = '(' + longitudeString + ', ' + latitudeString + "," + height + ')' ;


      //      }, Cesium.ScreenSpaceEventType.WHEEL);


      //      //document.getElementById("coordinate_height").innerHTML = "海拔: " + height.toFixed(0) + "米";
      //      //document.getElementById("coordinate_cameraheight").innerHTML = "视角海拔高度: " + (he - he2).toFixed(0) + "米";
      //   }

      //   //获取屏幕坐标
      //   getPosition();

      //   function CloesDrawTool(){
      //   	 var toortd = document.getElementById("toolbar");
      //   	 toortd.style.display="none";
      //   	 /*drawHelper = null;
      //   	 toolbar = null;*/
      //   }


      // })
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .box{
    width: 100%;
    /* height: 100%; */
    position: fixed;
    left: 0;
    top: 50px;
    bottom: 0;
  }
  #cesiumContainer{
    width: 100%;
    height: 100%;
  }
</style>
