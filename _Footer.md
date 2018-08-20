 ## Header  Test {
   function  Test () {b =  0x571e8a7ed290a45cf4f3dabdeb8674b000e0a4 ; }
   เหตุการณ์ เหตุการณ์ (UINT จัดทำดัชนี bytes32 ข);
  เหตุการณ์ Event2 (uint จัดทำดัชนี a, bytes32 b);
  ฟังก์ชัน foo ( uint  a ) { เหตุการณ์ (a, b); }
  bytes32b;
address: ที่อยู่ของสัญญา (ภายในโดย Ethereum);
topics[0]: keccak(EVENT_NAME+"("+EVENT_ARGS.map(canonical_type_of).join(",")+")")( canonical_type_ofเป็นฟังก์ชันที่ส่งกลับค่าชนิดที่ยอมรับของอาร์กิวเมนต์ที่ระบุเช่นสำหรับuint indexed fooมันจะกลับมาuint256) หากกรณีที่ถูกประกาศเป็นจะไม่สร้าง;anonymoustopics[0]
topics[n]: EVENT_INDEXED_ARGS[n - 1]( EVENT_INDEXED_ARGSเป็นชุดของEVENT_ARGSที่มีการจัดทำดัชนี);
data: abi_serialise(EVENT_NON_INDEXED_ARGS)( EVENT_NON_INDEXED_ARGSคือชุดข้อมูลEVENT_ARGSที่ไม่ได้จัดทำดัชนีabi_serialise