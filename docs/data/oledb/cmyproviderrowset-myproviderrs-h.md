---
title: CCustomRowset (CustomRS.H) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
- ccustomrowset
- customrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ee7aed5463054256d6903e485b83ce201a685d2
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807916"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

Kreator generuje wpis dla obiektu zestawu wierszy. W tym przypadku jest to `CCustomRowset`. `CCustomRowset` Klasa dziedziczy z klasy dostawcy OLE DB o nazwie `CRowsetImpl`, który implementuje wszystkie niezbędne interfejsy obiektu zestawu wierszy. Poniższy kod pokazuje łańcuch dziedziczenia dla `CRowsetImpl`:  
  
```cpp  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T >>  
```  
  
`CRowsetImpl` używa również `IAccessor` i `IColumnsInfo` interfejsów. Te interfejsy używa dla pól danych wyjściowych w tabelach. Ta klasa oferuje również implementację `IRowsetIdentity`, co pozwala, aby sprawdzić, czy dwa wiersze są identyczne. `IRowsetInfo` Interfejsu implementuje właściwości dla obiektu zestawu wierszy. `IConvertType` Interfejs umożliwia dostawcą rozwiązać różnice między typami danych żądanego przez klienta i używanych przez dostawcę.  
  
`IRowset` Interfejsu faktycznie obsługuje pobieranie danych. Konsument najpierw wywołuje metodę o nazwie `GetNextRows` do zwrócenia dojście do wiersza, znane jako `HROW`. Następnie wywołuje konsumenta `IRowset::GetData` z tym `HROW` można pobrać żądanych danych.  
  
`CRowsetImpl` pobiera również kilka parametrów szablonu. Parametry te umożliwiają ustalenie sposobu `CRowsetImpl` klasa służy do obsługi danych. `ArrayType` Argument pozwala określić, jakie mechanizm magazynu jest używane do przechowywania danych wiersza. *RowClass* parametr określa, jakie klasa zawiera `HROW`.  
  
*RowsetInterface* parametr umożliwia również `IRowsetLocate` lub `IRowsetScroll` interfejsu. `IRowsetLocate` i `IRowsetScroll` interfejsy, oba dziedziczyć `IRowset`. W związku z tym szablony dostawców OLE DB należy podać specjalnej obsługi tych interfejsów. Jeśli chcesz użyć jednej z tych interfejsów, należy użyć tego parametru.  
  
## <a name="see-also"></a>Zobacz też  

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)