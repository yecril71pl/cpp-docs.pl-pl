---
title: "Cnoaccessor — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
dev_langs:
- C++
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 02d577350a4a4221a2dcf9a8a3364de9ea4ce44e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cnoaccessor-class"></a>CNoAccessor — Klasa
Mogą być używane jako argument szablonu (`TAccessor`) dla klasy szablonów, takich jak `CCommand` i `CTable`, wymagających argumentu klasy metody dostępu.  
  
## <a name="syntax"></a>Składnia

```cpp
class CNoAccessor  
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CNoAccessor` jako argument szablonu nie można się z klasy do obsługi parametry lub kolumny wyjściowe.  
  
 `CNoAccessor` implementuje następujące metody klasy zastępczej, które odpowiadają innych metod klasy dostępu:  
  
-   **BindColumns** -wiąże kolumn metody dostępu.  
  
-   `BindParameters` — Wiąże utworzony parametry kolumny.  
  
-   **Powiąż** — tworzy wiązania.  
  
-   **Zamknij** -zamyka metodzie dostępu.  
  
-   `ReleaseAccessors` -Zwalnia akcesorów utworzone przez klasę.  
  
-   `FreeRecordMemory` -Zwalnia żadnych kolumn z bieżącego rekordu, który musi zostać zwolniony.  
  
-   `GetColumnInfo` -Pobiera informacji o kolumnie z otwartego zestawu wierszy.  
  
-   `GetNumAccessors` -Pobiera liczbę metod dostępu tworzone przez klasę.  
  
-   `IsAutoAccessor` -Zwraca wartość PRAWDA, jeśli dane są automatycznie pobierane dla metody dostępu podczas operacji przenoszenia.  
  
-   `GetHAccessor` -Pobiera dojście metody dostępu określonej metody dostępu.  
  
-   `GetBuffer` -Pobiera wskaźnik do buforu zakładki.  
  
-   **NoBindOnNullRowset** — uniemożliwia wiązania z danymi na pusty zestawów wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)