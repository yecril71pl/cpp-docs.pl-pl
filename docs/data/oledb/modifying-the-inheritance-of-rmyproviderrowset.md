---
title: Modyfikowanie dziedziczenia obiektu RCustomRowset | Dokumentacja firmy Microsoft
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
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a6f4827ecf0571878bc0eeaef5dce74326488c61
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990286"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>Modyfikowanie dziedziczenia obiektu RCustomRowset

Aby dodać `IRowsetLocate` interfejsu na przykładzie prostego dostawcy tylko do odczytu, modyfikowanie dziedziczenia obiektu `RCustomRowset`. Początkowo `RCustomRowset` dziedziczy `CRowsetImpl`. Należy zmodyfikować, aby dziedziczyć `CRowsetBaseImpl`.  
  
Aby to zrobić, Utwórz nową klasę, `CMyRowsetImpl`w *niestandardowe*RS.h:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// CustomRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>  
{  
...  
};  
```  
  
Teraz, Edytuj mapę interfejsu COM w *niestandardowe*RS.h są następujące:  
  
```cpp  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
Spowoduje to utworzenie mapę interfejsu COM, który informuje `CMyRowsetImpl` do wywołania `QueryInterface` dla obu `IRowset` i `IRowsetLocate` interfejsów. Aby uzyskać wszystkie wdrożenia w zestawie wierszy klas łącza mapy `CMyRowsetImpl` klasy z powrotem do `CRowsetBaseImpl` klasy zdefiniowane przez Szablony OLE DB; mapy używa makra COM_INTERFACE_ENTRY_CHAIN, która informuje o szablonach OLE DB do mapy COM w skanowania `CRowsetBaseImpl` w odpowiedzi na `QueryInterface` wywołania.  
  
Na koniec link `RAgentRowset` do `CMyRowsetBaseImpl` , modyfikując `RAgentRowset` odziedziczone `CMyRowsetImpl`, wykonując następujące czynności:  
  
```cpp  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CCustomCommand>  
```  
  
`RAgentRowset` można teraz używać `IRowsetLocate` interfejsu, wykorzystując pozostałe implementacji klasy zestawu wierszy.  
  
Po zakończeniu tej operacji możesz [dynamiczne określanie kolumn zwracanych do konsumenta](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Zobacz też  

[Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)