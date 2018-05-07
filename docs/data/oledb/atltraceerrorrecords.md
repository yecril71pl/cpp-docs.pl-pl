---
title: AtlTraceErrorRecords | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- AtlTraceErrorRecords function
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afea3c3ef1f169e5f1cb5fc675c74b54da1be0d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="atltraceerrorrecords"></a>AtlTraceErrorRecords
Zrzuty danych OLE DB Błąd rekordu do urządzenia zrzutu, jeśli zostanie zwrócony błąd.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hErr`  
 [in] `HRESULT` Zwracane przez funkcję elementu członkowskiego OLE DB szablon konsumenta.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `hErr` nie jest `S_OK`, `AtlTraceErrorRecords` zrzuty danych OLE DB Błąd rekordu do urządzenia zrzutu ( **debugowania** karty w oknie danych wyjściowych lub pliku). Rekord błędu informacje, które są uzyskiwane od dostawcy, obejmuje numer wiersza, źródło, opis, plik pomocy, kontekstu i identyfikator GUID dla każdego wpisu rekordów błąd. `AtlTraceErrorRecords` zrzuty te informacje tylko w kompilacjach debugowania. W kompilacjach wydania jest pusty stub zoptymalizowanego wychodzących.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo, klasa](../../data/oledb/cdberrorinfo-class.md)