# Система уведомления о коммерческих предложениях
Микросервисная система уведомления о коммерческих предложениях через kafka.
Позволяет отсылать уведомления пользователю, с защитой от падения отдельных компонентов системы.  
Состоит из 2х микросервисов:  
- NotificationKeeper  
- EmailNotificator

Подробно о каждом микросервисе написано в их личном репозитории

## Технологии  
- [Redis](https://redis.io/)  
- [InfluxDB](https://www.influxdata.com/)  
- [ApacheKafka](https://kafka.apache.org/)  
- [PostgreSQL](https://www.postgresql.org/)
- [Docker](https://www.docker.com)

## Как система выглядит, в общих чертах

{"type":"excalidraw/clipboard","elements":[{"id":"CV_aCS9MmuMxbYSo0-jPs","type":"rectangle","x":-296,"y":-168.2734375,"width":246,"height":322,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"#ffc9c9","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"frameId":null,"index":"a0","roundness":{"type":3},"seed":1044042607,"version":54,"versionNonce":1262166689,"isDeleted":false,"boundElements":[{"id":"u1qsknyPyZacz1LM_XlaV","type":"arrow"},{"id":"gk4DGvvqiwJUPJHvM7nDI","type":"arrow"},{"id":"1-v-Rqpv0-KDr0vDA_cdS","type":"arrow"},{"id":"i8QSfqd5xrb8UrYAGMyMP","type":"arrow"},{"id":"WoOmPIqFLFWonSdRErIze","type":"arrow"},{"id":"Nully0JPIYv_msjnRhG4B","type":"arrow"},{"id":"wrI8EK2AJWXHN8UGKFyNP","type":"arrow"}],"updated":1726305398617,"link":null,"locked":false},{"id":"fzIY8r2F","type":"text","x":-269.2645529174805,"y":-61.27343749999999,"width":203.7960662841797,"height":90,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"frameId":null,"index":"a2","roundness":null,"seed":40250561,"version":72,"versionNonce":1986585455,"isDeleted":false,"boundElements":null,"updated":1726303900659,"link":null,"locked":false,"text":"Notification\nKeeper","rawText":"Notification\nKeeper","fontSize":36,"fontFamily":1,"textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"Notification\nKeeper","lineHeight":1.25},{"id":"u1qsknyPyZacz1LM_XlaV","type":"arrow","x":-435,"y":-47.2734375,"width":137,"height":0,"angle":0,"strokeColor":"#f08c00","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"frameId":null,"index":"a3","roundness":{"type":2},"seed":111271439,"version":40,"versionNonce":1094736111,"isDeleted":false,"boundElements":null,"updated":1726304491134,"link":null,"locked":false,"points":[[0,0],[137,0]],"lastCommittedPoint":null,"startBinding":null,"endBinding":{"elementId":"CV_aCS9MmuMxbYSo0-jPs","focus":0.2484472049689441,"gap":2},"startArrowhead":null,"endArrowhead":"arrow"},{"id":"gk4DGvvqiwJUPJHvM7nDI","type":"arrow","x":-295,"y":17.7265625,"width":138,"height":0,"angle":0,"strokeColor":"#f08c00","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"groupIds":[],"frameId":null,"index":"a4","roundness":{"type":2},"seed":610136449,"version":60,"versionNonce":1392597345,"isDeleted":false,"boundElements":null,"updated":1726304493745,"link":null,"locked":false,"points":[[0,0],[-138,0]],"lastCommittedPoint":null,"startBinding":{"elementId":"CV_aCS9MmuMxbYSo0-jPs","focus":-0.15527950310559005,"gap":1},"endBinding":null,"startArrowhead":null,"endArrowhead":"arrow"},{"id":"wnzCXgsZBaVfUATAMR17V","type":"rectangle","x":30.904761904761926,"y":-330.1299452853008,"width":444.61538461538487,"height":565.9728506787333,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"groupIds":["WwQSG26fhox6NhW27sBmm"],"frameId":null,"index":"a5","roundness":{"type":3},"seed":1065469729,"version":203,"versionNonce":416188879,"isDeleted":false,"boundElements":null,"updated":1726304477896,"link":null,"locked":false},{"id":"4wZKIKGI","type":"text","x":212.19089530413862,"y":-282.437637592993,"width":105.12004089355469,"height":45,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"groupIds":["WwQSG26fhox6NhW27sBmm"],"frameId":null,"index":"a6","roundness":null,"seed":157855393,"version":121,"versionNonce":143851169,"isDeleted":false,"boundElements":null,"updated":1726304477896,"link":null,"locked":false,"text":"Kafka","rawText":"Kafka","fontSize":36,"fontFamily":1,"textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"Kafka","lineHeight":1.25},{"id":"D8mNzYvXyajbfXIWF-QvK","type":"rectangle","x":56.334626158155515,"y":-207.32451542104718,"width":389.2307692307694,"height":198.46153846153857,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"groupIds":["ME2rP8_iKeGgsux4EBa1R","WwQSG26fhox6NhW27sBmm"],"frameId":null,"index":"a7","roundness":{"type":3},"seed":1193409409,"version":183,"versionNonce":1025144815,"isDeleted":false,"boundElements":[{"id":"1-v-Rqpv0-KDr0vDA_cdS","type":"arrow"},{"id":"A8Xv19t63Rf6Fh-CWyorQ","type":"arrow"}],"updated":1726304477896,"link":null,"locked":false},{"type":"rectangle","version":245,"versionNonce":299664001,"index":"a8","isDeleted":false,"id":"QFWx_i4lyC8orSxHOga5P","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"angle":0,"x":58.642318465847836,"y":10.367792271260555,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","width":389.2307692307694,"height":198.46153846153857,"seed":127668129,"groupIds":["ME2rP8_iKeGgsux4EBa1R","WwQSG26fhox6NhW27sBmm"],"frameId":null,"roundness":{"type":3},"boundElements":[{"id":"i8QSfqd5xrb8UrYAGMyMP","type":"arrow"},{"id":"K7FsbL7OI-ux_zWi9vskW","type":"arrow"}],"updated":1726304477896,"link":null,"locked":false},{"id":"g6Cnx9Tz","type":"text","x":152.31992623662677,"y":-165.33356519480265,"width":187.2699503181805,"height":112.3529411764705,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"groupIds":["ME2rP8_iKeGgsux4EBa1R","WwQSG26fhox6NhW27sBmm"],"frameId":null,"index":"a9","roundness":null,"seed":590668193,"version":209,"versionNonce":1778622991,"isDeleted":false,"boundElements":null,"updated":1726304477896,"link":null,"locked":false,"text":"Command\nTopic","rawText":"Command\nTopic","fontSize":44.94117647058819,"fontFamily":1,"textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"Command\nTopic","lineHeight":1.25},{"type":"text","version":258,"versionNonce":1661635169,"index":"aA","isDeleted":false,"id":"v8SThNFL","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"angle":0,"x":171.5674336685546,"y":42.01937598166796,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","width":146.8111572265625,"height":112.35294117647047,"seed":1784935873,"groupIds":["ME2rP8_iKeGgsux4EBa1R","WwQSG26fhox6NhW27sBmm"],"frameId":null,"roundness":null,"boundElements":[],"updated":1726304477896,"link":null,"locked":false,"fontSize":44.94117647058819,"fontFamily":1,"text":"Report\nTopic","rawText":"Report\nTopic","textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"Report\nTopic","lineHeight":1.25},{"id":"1-v-Rqpv0-KDr0vDA_cdS","type":"arrow","x":-51.49757595345807,"y":-86.51003578303812,"width":104.70588235294122,"height":0,"angle":0,"strokeColor":"#1971c2","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aC","roundness":{"type":2},"seed":207596815,"version":54,"versionNonce":176203425,"isDeleted":false,"boundElements":null,"updated":1726304371749,"link":null,"locked":false,"points":[[0,0],[104.70588235294122,0]],"lastCommittedPoint":null,"startBinding":{"elementId":"CV_aCS9MmuMxbYSo0-jPs","focus":-0.49215278436669646,"gap":1},"endBinding":{"elementId":"D8mNzYvXyajbfXIWF-QvK","focus":-0.21751025991792014,"gap":3.1263197586723663},"startArrowhead":null,"endArrowhead":"arrow"},{"id":"i8QSfqd5xrb8UrYAGMyMP","type":"arrow","x":57.914188752424366,"y":69.96055245225602,"width":104.70588235294122,"height":0,"angle":0,"strokeColor":"#1971c2","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aD","roundness":{"type":2},"seed":1198410913,"version":47,"versionNonce":457800207,"isDeleted":false,"boundElements":null,"updated":1726304374016,"link":null,"locked":false,"points":[[0,0],[-104.70588235294122,0]],"lastCommittedPoint":null,"startBinding":{"elementId":"QFWx_i4lyC8orSxHOga5P","focus":0.39945280437756536,"gap":1},"endBinding":{"elementId":"CV_aCS9MmuMxbYSo0-jPs","focus":0.47971422330593805,"gap":3.208306399483149},"startArrowhead":null,"endArrowhead":"arrow"},{"type":"rectangle","version":89,"versionNonce":1216068687,"index":"aE","isDeleted":false,"id":"06e49bk0VaO-l2t-6Nc2G","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":586.8406593406595,"y":-177.01003578303823,"strokeColor":"#1e1e1e","backgroundColor":"#ffc9c9","width":246,"height":322,"seed":1295521455,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[{"id":"A8Xv19t63Rf6Fh-CWyorQ","type":"arrow"},{"id":"K7FsbL7OI-ux_zWi9vskW","type":"arrow"},{"id":"cr-qNdOiJLiFUSS_bDmSf","type":"arrow"},{"id":"bS2TunIF8nJhBRRZrvH-f","type":"arrow"},{"id":"8j9C-hmaPUYz2CLGF2U-n","type":"arrow"},{"id":"RdBZ5HkYPymbtyrXCfTq1","type":"arrow"}],"updated":1726305748990,"link":null,"locked":false},{"type":"text","version":125,"versionNonce":536450127,"index":"aF","isDeleted":false,"id":"ClRkSi7O","fillStyle":"solid","strokeWidth":2,"strokeStyle":"solid","roughness":1,"opacity":100,"angle":0,"x":618.1841081321634,"y":-70.01003578303823,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":194.58006286621094,"height":90,"seed":1249863887,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1726304428336,"link":null,"locked":false,"fontSize":36,"fontFamily":1,"text":"Email\nNotificator","rawText":"Email\nNotificator","textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"Email\nNotificator","lineHeight":1.25},{"id":"A8Xv19t63Rf6Fh-CWyorQ","type":"arrow","x":444.507326007326,"y":-73.3433691163716,"width":138.66666666666674,"height":0,"angle":0,"strokeColor":"#1971c2","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aH","roundness":{"type":2},"seed":408029153,"version":38,"versionNonce":1610295073,"isDeleted":false,"boundElements":null,"updated":1726304442842,"link":null,"locked":false,"points":[[0,0],[138.66666666666674,0]],"lastCommittedPoint":null,"startBinding":{"elementId":"D8mNzYvXyajbfXIWF-QvK","focus":0.3501975984192106,"gap":1},"endBinding":{"elementId":"06e49bk0VaO-l2t-6Nc2G","focus":0.35610766045548675,"gap":3.6666666666667425},"startArrowhead":null,"endArrowhead":"arrow"},{"id":"K7FsbL7OI-ux_zWi9vskW","type":"arrow","x":585.8406593406595,"y":59.989964216961766,"width":136.00000000000023,"height":0,"angle":0,"strokeColor":"#1971c2","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aI","roundness":{"type":2},"seed":1127240079,"version":33,"versionNonce":1521702287,"isDeleted":false,"boundElements":null,"updated":1726304454341,"link":null,"locked":false,"points":[[0,0],[-136.00000000000023,0]],"lastCommittedPoint":null,"startBinding":{"elementId":"06e49bk0VaO-l2t-6Nc2G","focus":-0.4720496894409939,"gap":1},"endBinding":{"elementId":"QFWx_i4lyC8orSxHOga5P","focus":-0.4999316005471972,"gap":1.9675716440420388},"startArrowhead":null,"endArrowhead":"arrow"},{"type":"rectangle","version":299,"versionNonce":1770461455,"index":"aL","isDeleted":false,"id":"N76B8Sy-IVWF4X7egw3mB","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":24.507326007326014,"y":257.323297550295,"strokeColor":"#1971c2","backgroundColor":"#a5d8ff","width":460,"height":200.00000000000006,"seed":763072513,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[{"id":"WoOmPIqFLFWonSdRErIze","type":"arrow"},{"id":"cr-qNdOiJLiFUSS_bDmSf","type":"arrow"}],"updated":1726304628588,"link":null,"locked":false},{"id":"WoOmPIqFLFWonSdRErIze","type":"arrow","x":-151.47364572869793,"y":151.9968812739451,"width":174.62308211663267,"height":234.65969854916594,"angle":0,"strokeColor":"#1971c2","backgroundColor":"#a5d8ff","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aM","roundness":null,"seed":1438061743,"version":156,"versionNonce":1773429263,"isDeleted":false,"boundElements":null,"updated":1726304861455,"link":null,"locked":false,"points":[[2.1148191436815603e-16,0],[-2.842170943040401e-14,231.7626652337443],[174.62308211663265,234.65969854916594]],"lastCommittedPoint":null,"startBinding":{"elementId":"CV_aCS9MmuMxbYSo0-jPs","focus":-0.17501101033578925,"gap":1},"endBinding":{"elementId":"ozXPg3i6MqHWhmz6-kbzj","focus":-0.20185449692327928,"gap":8.024556286057816},"startArrowhead":null,"endArrowhead":"arrow"},{"id":"cr-qNdOiJLiFUSS_bDmSf","type":"arrow","x":719.1699540757347,"y":147.93966435613947,"width":229.42972141514832,"height":226.6835972113594,"angle":0,"strokeColor":"#1971c2","backgroundColor":"#a5d8ff","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aN","roundness":null,"seed":436328527,"version":154,"versionNonce":1733174639,"isDeleted":false,"boundElements":null,"updated":1726304857117,"link":null,"locked":false,"points":[[-1.2369452515184207,0],[-1.2369452515184207,225.21162580089586],[-230.66666666666674,226.6835972113594]],"lastCommittedPoint":null,"startBinding":{"elementId":"06e49bk0VaO-l2t-6Nc2G","focus":-0.06579145921590944,"gap":2.9497001391777076},"endBinding":{"elementId":"ozXPg3i6MqHWhmz6-kbzj","focus":-0.06008823463114173,"gap":19.995961401741965},"startArrowhead":null,"endArrowhead":"arrow"},{"type":"rectangle","version":400,"versionNonce":50114767,"index":"aO","isDeleted":false,"id":"9pRF76ciHsum4Or6JQgdI","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":587.173992673993,"y":-486.6767024497051,"strokeColor":"#1971c2","backgroundColor":"#a5d8ff","width":228.00000000000006,"height":101.33333333333337,"seed":298131297,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[{"id":"bS2TunIF8nJhBRRZrvH-f","type":"arrow"},{"id":"8j9C-hmaPUYz2CLGF2U-n","type":"arrow"}],"updated":1726305311415,"link":null,"locked":false},{"type":"rectangle","version":549,"versionNonce":528233487,"index":"aP","isDeleted":false,"id":"4C9onZioy6icWMS76n8kE","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":26.50732600732573,"y":-482.676702449705,"strokeColor":"#1971c2","backgroundColor":"#a5d8ff","width":438.6666666666668,"height":129.33333333333337,"seed":876639457,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[{"id":"Nully0JPIYv_msjnRhG4B","type":"arrow"},{"id":"wrI8EK2AJWXHN8UGKFyNP","type":"arrow"},{"id":"RdBZ5HkYPymbtyrXCfTq1","type":"arrow"}],"updated":1726305748989,"link":null,"locked":false},{"type":"rectangle","version":530,"versionNonce":1286518433,"index":"aS","isDeleted":false,"id":"ON3x2I9yoJadmpRiOnyBr","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":-284.15934065934084,"y":-485.3433691163718,"strokeColor":"#1971c2","backgroundColor":"#a5d8ff","width":228.00000000000006,"height":105.3333333333334,"seed":519569281,"groupIds":[],"frameId":null,"roundness":{"type":3},"boundElements":[],"updated":1726304932082,"link":null,"locked":false},{"id":"IaaA5YJy","type":"text","x":181.34328639550955,"y":277.32329755029525,"width":158.3280792236328,"height":45,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aT","roundness":null,"seed":545277519,"version":72,"versionNonce":1194381601,"isDeleted":false,"boundElements":null,"updated":1726304792221,"link":null,"locked":false,"text":"InfluxDB","rawText":"InfluxDB","fontSize":36,"fontFamily":1,"textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"InfluxDB","lineHeight":1.25},{"id":"ACFSS0td","type":"text","x":218.2946464622413,"y":357.323297550295,"width":79.09202575683594,"height":45,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"#a5d8ff","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aU","roundness":null,"seed":1698020577,"version":91,"versionNonce":1529024257,"isDeleted":false,"boundElements":null,"updated":1726304839752,"link":null,"locked":false,"text":"Logs","rawText":"Logs","fontSize":36,"fontFamily":1,"textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"Logs","lineHeight":1.25},{"id":"ozXPg3i6MqHWhmz6-kbzj","type":"rectangle","x":31.17399267399253,"y":327.98996421696177,"width":437.3333333333335,"height":102.66666666666674,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aV","roundness":{"type":3},"seed":821593057,"version":84,"versionNonce":1545291823,"isDeleted":false,"boundElements":[{"id":"cr-qNdOiJLiFUSS_bDmSf","type":"arrow"},{"id":"WoOmPIqFLFWonSdRErIze","type":"arrow"}],"updated":1726304861455,"link":null,"locked":false},{"id":"BCQA5jrQ","type":"text","x":-275.7302205453652,"y":-456.78196560759966,"width":205.66807556152344,"height":45,"angle":0,"strokeColor":"#1e1e1e","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aW","roundness":null,"seed":463514895,"version":42,"versionNonce":146167329,"isDeleted":false,"boundElements":null,"updated":1726305034877,"link":null,"locked":false,"text":"PostgreSQL","rawText":"PostgreSQL","fontSize":36,"fontFamily":1,"textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"PostgreSQL","lineHeight":1.25},{"type":"text","version":134,"versionNonce":47768687,"index":"aX","isDeleted":false,"id":"QaLGeOcj","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"angle":0,"x":602.16451629674,"y":-457.1767024497049,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":205.66807556152344,"height":45,"seed":1289617889,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1726305041228,"link":null,"locked":false,"fontSize":36,"fontFamily":1,"text":"PostgreSQL","rawText":"PostgreSQL","textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"PostgreSQL","lineHeight":1.25},{"type":"text","version":175,"versionNonce":1240850561,"index":"ae","isDeleted":false,"id":"GmAnj4di","fillStyle":"solid","strokeWidth":4,"strokeStyle":"dashed","roughness":2,"opacity":100,"angle":0,"x":204.98512525658737,"y":-438.76106777478213,"strokeColor":"#1e1e1e","backgroundColor":"transparent","width":92.01602172851562,"height":45,"seed":1236374241,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1726305279153,"link":null,"locked":false,"fontSize":36,"fontFamily":1,"text":"Redis","rawText":"Redis","textAlign":"center","verticalAlign":"top","containerId":null,"originalText":"Redis","lineHeight":1.25},{"id":"bS2TunIF8nJhBRRZrvH-f","type":"arrow","x":701.659802787512,"y":-381.3433690000001,"width":0,"height":201.08230122521792,"angle":0,"strokeColor":"#1971c2","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"ak","roundness":{"type":2},"seed":13005889,"version":145,"versionNonce":1155649263,"isDeleted":false,"boundElements":null,"updated":1726305328195,"link":null,"locked":false,"points":[[0,0],[0,201.08230122521792]],"lastCommittedPoint":null,"startBinding":{"elementId":"9pRF76ciHsum4Or6JQgdI","focus":-0.004261492223850325,"gap":4.000000116371609},"endBinding":{"elementId":"06e49bk0VaO-l2t-6Nc2G","focus":-0.06651102888737775,"gap":3.2510319917439574},"startArrowhead":null,"endArrowhead":"arrow"},{"type":"arrow","version":339,"versionNonce":832577327,"index":"al","isDeleted":false,"id":"8j9C-hmaPUYz2CLGF2U-n","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":748.293021762008,"y":-179.12795473856585,"strokeColor":"#1971c2","backgroundColor":"transparent","width":0,"height":199.79977970288303,"seed":115391055,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1726305328196,"link":null,"locked":false,"startBinding":{"elementId":"06e49bk0VaO-l2t-6Nc2G","focus":0.31262083269389057,"gap":2.117918955527614},"endBinding":{"elementId":"9pRF76ciHsum4Or6JQgdI","focus":-0.41332481656153447,"gap":6.415634674922842},"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[0,-199.79977970288303]]},{"type":"arrow","version":189,"versionNonce":1310261935,"index":"ao","isDeleted":false,"id":"r4-rU6kuEpdPc6wCc2jgr","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":-249.85345093249362,"y":-374.2284607992173,"strokeColor":"#1971c2","backgroundColor":"transparent","width":0,"height":201.08230122521792,"seed":2058837871,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1726305331048,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[0,201.08230122521792]]},{"type":"arrow","version":383,"versionNonce":1482872015,"index":"ap","isDeleted":false,"id":"eZnzaUZCtL4ghLzwm6YH-","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":-203.2202319579976,"y":-172.01304653778305,"strokeColor":"#1971c2","backgroundColor":"transparent","width":0,"height":199.79977970288303,"seed":1117231503,"groupIds":[],"frameId":null,"roundness":{"type":2},"boundElements":[],"updated":1726305331048,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[0,0],[0,-199.79977970288303]]},{"id":"Nully0JPIYv_msjnRhG4B","type":"arrow","x":25.659802787511808,"y":-416.26106777478213,"width":136.0000000000001,"height":238.66666666666669,"angle":0,"strokeColor":"#1971c2","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"groupIds":[],"frameId":null,"index":"aq","roundness":null,"seed":1781149167,"version":522,"versionNonce":709665217,"isDeleted":false,"boundElements":null,"updated":1726305389817,"link":null,"locked":false,"points":[[0,0],[-85.33333333333348,44],[-136.0000000000001,238.66666666666669]],"lastCommittedPoint":null,"startBinding":{"elementId":"4C9onZioy6icWMS76n8kE","focus":0.6288339566708578,"gap":1},"endBinding":{"elementId":"CV_aCS9MmuMxbYSo0-jPs","focus":0.11115362144327659,"gap":9.320963608115449},"startArrowhead":null,"endArrowhead":"arrow"},{"type":"arrow","version":643,"versionNonce":1064066561,"index":"ar","isDeleted":false,"id":"wrI8EK2AJWXHN8UGKFyNP","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":24.22153230741796,"y":-373.7891672066815,"strokeColor":"#1971c2","backgroundColor":"transparent","width":106.66666666666674,"height":201.33333333333331,"seed":1965712623,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1726305404374,"link":null,"locked":false,"startBinding":{"elementId":"4C9onZioy6icWMS76n8kE","focus":-0.1964978610878095,"gap":2.285793699907771},"endBinding":{"elementId":"CV_aCS9MmuMxbYSo0-jPs","focus":0.28842329794660465,"gap":4.182396373348183},"lastCommittedPoint":null,"startArrowhead":"arrow","endArrowhead":null,"points":[[0,0],[-56.000000000000114,6.666666666666629],[-106.66666666666674,201.33333333333331]]},{"type":"arrow","version":735,"versionNonce":1325910593,"index":"au","isDeleted":false,"id":"h9FRenIrGYErHJcPxUW57","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":605.6808110361183,"y":-407.5973863936215,"strokeColor":"#1971c2","backgroundColor":"transparent","width":177.5665684481477,"height":225.22996523357088,"seed":105106607,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1726305446379,"link":null,"locked":false,"startBinding":null,"endBinding":null,"lastCommittedPoint":null,"startArrowhead":null,"endArrowhead":"arrow","points":[[-136.0000000000001,0],[-24.585682542338716,41.52284275255776],[41.56656844814758,225.22996523357088]]},{"type":"arrow","version":883,"versionNonce":1830345263,"index":"av","isDeleted":false,"id":"RdBZ5HkYPymbtyrXCfTq1","fillStyle":"solid","strokeWidth":4,"strokeStyle":"solid","roughness":2,"opacity":100,"angle":0,"x":467.5318938895415,"y":-379.79451820364966,"strokeColor":"#1971c2","backgroundColor":"transparent","width":155.94776061928567,"height":200.03824232201563,"seed":346316495,"groupIds":[],"frameId":null,"roundness":null,"boundElements":[],"updated":1726305748990,"link":null,"locked":false,"startBinding":{"elementId":"4C9onZioy6icWMS76n8kE","focus":-0.3589466494270865,"gap":2.3579012155489636},"endBinding":{"elementId":"06e49bk0VaO-l2t-6Nc2G","focus":-0.13820805348969833,"gap":2.7462400985957913},"lastCommittedPoint":null,"startArrowhead":"arrow","endArrowhead":null,"points":[[0,0],[96.87257432512513,41.62378285834484],[155.94776061928567,200.03824232201563]]}],"files":{}}

  
## Использование  
  
Для запуска приложения, нужно поднять необходимые контейнеры с помощью docker-compose.  
Для этого в папке проекта нужно вызвать команду docker compose up. (При его отсутствии, его нужно установить)  

Для отправки уведомления, нужно отправить HTTP запрос на URL:  
http://localhost:8080/api/v1.0/Notification/  
Метод POST  
Тело запроса:  
{  
"BlueprintId" : "...",  
"CustomerId" : "..."  
}  
  
Инициализирующие данные:  
CustomerId: a7f1cf1f-5f4f-4159-99cc-80a4e9f7c5cb  
BlueprintId: b7f1cf1f-5f4f-4159-99cc-80a4e9f7c5cb  
