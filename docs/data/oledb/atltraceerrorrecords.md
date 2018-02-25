---
title: AtlTraceErrorRecords | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 024a4331b71b3414aa7d83f27ecaca4e5d2f11de
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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