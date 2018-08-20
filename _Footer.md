 ## Header  Test {
   function  Test () {b =  0x571e8a7ed290a45cf4f3dabdeb8674b000e0a4 ; }
   เหตุการณ์ เหตุการณ์ (UINT จัดทำดัชนี bytes32 ข);
  เหตุการณ์ Event2 (uint จัดทำดัชนี a, bytes32 b);
  ฟังก์ชัน foo ( uint  a ) { เหตุการณ์ (a, b); }
  bytes32b;
varทดสอบ= ผลประโยชน์ทับซ้อน สัญญา (
[{
" type " : " event " ,
 " inputs " : [{ " name " : " a " , " type " : " uint256 " , " indexed " : true }, { " name " : " b " , " type " : " bytes32 " , "จัดทำดัชนี" : เท็จ}],
 " name " : " Event "
}, {
" type " : " event " ,
 " inputs " : [{ " name " : " a " , " type " : " uint256 " , " indexed " : true }, { " name " : " b " , " type " : " bytes32 " , "จัดทำดัชนี" : เท็จ}],
 " name " : " Event2 "
}, {
"ชนิด" : "ฟังก์ชัน" ,
 "อินพุต" : [{ "ชื่อ" : " a " , " type " : " uint256 " }],
 " name " : " foo " ,
 " outputs " : []
}]);
var theTest =  test ใหม่  (addrTest);

//ตัวอย่างของการใช้งาน: 
//รายการบันทึกทุก ( "เหตุการณ์") มาจาก thetest (เช่นจัด Event2): 
var F0 = ผลประโยชน์ทับซ้อน กรอง (theTest);
//เพียงเข้าสู่ระบบรายการ ( "เหตุการณ์") ประเภท "งาน" มาจาก thetest: 
var f1 = ผลประโยชน์ทับซ้อน กรอง ( theTest . Event );
//ยังเขียนเป็น
var f1 =  thetest เหตุการณ์ ();
//เพียงบันทึกรายการ ("events") ของ "Event" และ "Event2" ที่มาจาก theTest:
 eth . กรอง ([ theTest . Event , theTest . Event2 ]);
//เพียงเข้าสู่ระบบรายการ ( "เหตุการณ์") ประเภท "งาน" มาจาก thetest กับพารามิเตอร์การจัดทำดัชนี 'a' เท่ากับ 69: 
var f3 = ผลประโยชน์ทับซ้อน กรอง ( theTest . Event , { ' a ' :  69 });
//ยังเขียนเป็น
var f3 =  thetest เหตุการณ์ ({ ' a ' :  69 });
//เพียงเข้าสู่ระบบรายการ ( "เหตุการณ์") ประเภท "งาน" มาจาก thetest กับพารามิเตอร์การจัดทำดัชนี 'a' เท่ากับ 69 หรือ 42: 
var f4 = ผลประโยชน์ทับซ้อน กรอง ( theTest . Event , { ' a ' : [ 69 , 42 ]});
//ยังเขียนเป็น
var f4 =  thetest เหตุการณ์ ({ ' a ' : [ 69 , 42 ]});

//ตัวเลือกอาจมีให้เป็นพารามิเตอร์ที่สองด้วย `เร็ว ',` ล่าสุด', `ออฟเซ็ท 'และ` สูงสุด' ตามที่กำหนดไว้สำหรับ `eth.filter` 
var options = { ' max ' :  100 };
var f4 =  thetest เหตุการณ์ ({ ' a ' : [ 69 , 42 ]}, ตัวเลือก);

เรียกvar ;
f4 นาฬิกา (ทริกเกอร์);

//โทร foo ที่จะทำให้เหตุการณ์:
 thetest foo ( 69 );

//จะเรียก trigger เช่น: 
// trigger (theTest.Event, {'a': 69, 'b': '0x571e8a7ed290a45cf4f3dabdeb8674b000e0a4'}, n); 
//ที่ n คือหมายเลขบล็อคที่เหตุการณ์ถูกเรียกใช้
<!--*Name Surname*, Github username, **email@domain** and/or other contact methods-->