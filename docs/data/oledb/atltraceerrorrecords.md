---
title: AtlTraceErrorRecords | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
dev_langs: C++
helpviewer_keywords: AtlTraceErrorRecords function
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a3f8542f2c897f45916ac62fbac147259b2362d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atltraceerrorrecords"></a>AtlTraceErrorRecords
Zrzuty danych OLE DB Błąd rekordu do urządzenia zrzutu, jeśli zostanie zwrócony błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      inline void AtlTraceErrorRecords(   
   HRESULT hrErr = S_OK    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hErr`  
 [in] `HRESULT` Zwracane przez funkcję elementu członkowskiego OLE DB szablon konsumenta.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `hErr` nie jest `S_OK`, `AtlTraceErrorRecords` zrzuty danych OLE DB Błąd rekordu do urządzenia zrzutu ( **debugowania** karty w oknie danych wyjściowych lub pliku). Rekord błędu informacje, które są uzyskiwane od dostawcy, obejmuje numer wiersza, źródło, opis, plik pomocy, kontekstu i identyfikator GUID dla każdego wpisu rekordów błąd. `AtlTraceErrorRecords`zrzuty te informacje tylko w kompilacjach debugowania. W kompilacjach wydania jest pusty stub zoptymalizowanego wychodzących.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo, klasa](../../data/oledb/cdberrorinfo-class.md)