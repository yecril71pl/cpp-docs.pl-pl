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
ms.openlocfilehash: 77b26d1d0b67726e1ba2cd66d0e181bc04105a6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028171"
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>Modyfikowanie dziedziczenia obiektu RMyProviderRowset

Aby dodać `IRowsetLocate` interfejsu na przykładzie prostego dostawcy tylko do odczytu, modyfikowanie dziedziczenia obiektu `RMyProviderRowset`. Początkowo `RMyProviderRowset` dziedziczy `CRowsetImpl`. Należy zmodyfikować, aby dziedziczyć `CRowsetBaseImpl`.  
  
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
  
```cpp  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
Spowoduje to utworzenie mapę interfejsu COM, który informuje `CMyRowsetImpl` do wywołania `QueryInterface` dla obu `IRowset` i `IRowsetLocate` interfejsów. Aby uzyskać wszystkie wdrożenia w zestawie wierszy klas łącza mapy `CMyRowsetImpl` klasy z powrotem do `CRowsetBaseImpl` klasy zdefiniowane przez Szablony OLE DB; mapy używa makra COM_INTERFACE_ENTRY_CHAIN, która informuje o szablonach OLE DB do mapy COM w skanowania `CRowsetBaseImpl` w odpowiedzi na `QueryInterface` wywołania.  
  
Na koniec link `RAgentRowset` do `CMyRowsetBaseImpl` , modyfikując `RAgentRowset` odziedziczone `CMyRowsetImpl`, wykonując następujące czynności:  
  
```cpp  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
`RAgentRowset` można teraz używać `IRowsetLocate` interfejsu, wykorzystując pozostałe implementacji klasy zestawu wierszy.  
  
Po zakończeniu tej operacji możesz [dynamiczne określanie kolumn zwracanych do konsumenta](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Zobacz też  

[Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)