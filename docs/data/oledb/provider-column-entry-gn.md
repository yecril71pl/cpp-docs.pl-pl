---
title: PROVIDER_COLUMN_ENTRY_GN | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROVIDER_COLUMN_ENTRY_GN
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_GN macro
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 203f339dc031f4a21f16181043b051c4eaa5ec35
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="providercolumnentrygn"></a>PROVIDER_COLUMN_ENTRY_GN
Przedstawia kolumnę określonych obsługiwane przez dostawcę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 [in] Nazwa kolumny.  
  
 `ordinal`  
 [in] Numer kolumny. Jeśli kolumna jest kolumną zakładki, numer kolumny nie może być 0.  
  
 `flags`  
 [in] Określa, jak dane są zwracane. Zobacz `dwFlags` opis w [struktury DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *colSize*  
 [in] Rozmiar kolumny.  
  
 `dbtype`  
 [in] Wskazuje typ danych wartości. Zobacz **wType** opis w [struktury DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *dokładność*  
 [in] Wskazuje dokładność do użycia podczas pobierania danych, jeśli *dbType* jest `DBTYPE_NUMERIC` lub **DBTYPE_DECIMAL**. Zobacz **bPrecision** opis w [struktury DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `scale`  
 [in] Wskazuje skali do użycia podczas pobierania danych, jeśli jest dbType `DBTYPE_NUMERIC` lub **DBTYPE_DECIMAL**. Zobacz **bScale** opis w [struktury DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `guid`  
 Zestaw wierszy schematu identyfikatora GUID. Zobacz [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w *OLE DB Podręcznik programisty* listę zestawów wierszy schematu i ich identyfikatorów GUID.  
  
## <a name="remarks"></a>Uwagi  
 Umożliwia określenie kolumny rozmiar, typ danych precyzja, skala i identyfikatorem GUID zestawu wierszy schematu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)