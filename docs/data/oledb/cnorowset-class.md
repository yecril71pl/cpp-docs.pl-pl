---
title: "Cnorowset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs: C++
helpviewer_keywords: CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 678c2483a3ac22999ba0219b4f87392d81e03ea7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cnorowset-class"></a>CNoRowset — Klasa
Mogą być używane jako argument szablonu (`TRowset`) dla [CCommand](../../data/oledb/ccommand-class.md) lub [CTable](../../data/oledb/ctable-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Klasa metody dostępu. Wartość domyślna to `CAccessorBase`.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CNoRowset` jako argument szablonu, jeśli polecenie nie zwraca zestawu wierszy.  
  
 `CNoRowset`implementuje następujące metody klasy zastępczej, które odpowiadają innych metod klasy dostępu:  
  
-   **BindFinished** — wskazuje, po zakończeniu wiązania (zwraca `S_OK`).  
  
-   **Zamknij** -zwalnia wierszy i bieżącego interfejsu IRowset.  
  
-   `GetIID`-Pobiera identyfikator interfejsu punktu połączenia.  
  
-   **GetInterface** -pobiera interfejs.  
  
-   `GetInterfacePtr`-Pobiera wskaźnika hermetyzowany interfejsu.  
  
-   **SetAccessor** -ustawia wskaźnik na metodzie dostępu.  
  
-   **SetupOptionalRowsetInterfaces** -ustawia opcjonalne interfejsów dla zestawu wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)