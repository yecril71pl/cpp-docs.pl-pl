---
title: BEGIN_PROPSET_MAP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_PROPSET_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPSET_MAP macro
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b1596797672c0fff92531ff90f67b94bfd6101e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089467"
---
# <a name="beginpropsetmap"></a>BEGIN_PROPSET_MAP
Znaki na początku właściwości ustaw wpisów map.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *Class*  
 [in] Określono klasy, w którym ta właściwość jest ustawiona. Zestaw właściwości można określić w następujących obiektów OLE DB:  
  
-   [Obiekty źródła danych](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [Obiektów sesji](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [Polecenia](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## <a name="example"></a>Przykład  
 Oto przykładowe mapy zestaw właściwości:  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)