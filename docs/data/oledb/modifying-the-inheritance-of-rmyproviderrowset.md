---
title: Modyfikowanie dziedziczenia obiektu RMyProviderRowset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75acbc8370c1ea164c72aa6f0c61a95fe287e3d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>Modyfikowanie dziedziczenia obiektu RMyProviderRowset
Aby dodać `IRowsetLocate` interfejsu, na przykład prostego dostawcy tylko do odczytu, modyfikowanie dziedziczenia obiektu **RMyProviderRowset**. Początkowo **RMyProviderRowset** dziedziczy `CRowsetImpl`. Należy zmodyfikować, aby dziedziczyć z **CRowsetBaseImpl**.  
  
 Aby to zrobić, Utwórz nową klasę, `CMyRowsetImpl`, w MyProviderRS.h:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>  
{  
...  
};  
```  
  
 Teraz Edytuj mapę interfejsu COM w MyProviderRS.h są następujące:  
  
```  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 Spowoduje to utworzenie mapy interfejsu COM, informujący o `CMyRowsetImpl` do wywołania **QueryInterface** dla obu `IRowset` i `IRowsetLocate` interfejsów. Do pobrania wszystkich implementacją w zestawie wierszy klas, łącza mapy `CMyRowsetImpl` klasy z powrotem do **CRowsetBaseImpl** klasa zdefiniowana przez Szablony OLE DB; mapy korzysta z makra COM_INTERFACE_ENTRY_CHAIN, która informuje Szablony OLE DB do skanowania modelu COM mapy w **CRowsetBaseImpl** w odpowiedzi na `QueryInterface` wywołania.  
  
 Na koniec link `RAgentRowset` do `CMyRowsetBaseImpl` , modyfikując `RAgentRowset` odziedziczone `CMyRowsetImpl`w następujący sposób:  
  
```  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset` można teraz używać `IRowsetLocate` interfejsu, wykorzystując pozostałe implementacji klasy zestawu wierszy.  
  
 Jeśli zostanie to zrobione, możesz [dynamiczne określanie kolumn zwracanych do konsumenta](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)