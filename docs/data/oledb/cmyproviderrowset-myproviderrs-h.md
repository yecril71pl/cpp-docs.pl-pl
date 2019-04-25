---
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
- ccustomrowset
- customrs.h
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 9f9dcb97ecd6b5f37f1af2187abf8b5612eedce3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230666"
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

`CRowsetImpl` używa również `IAccessor` i `IColumnsInfo` interfejsów. Te interfejsy używa dla pól danych wyjściowych w tabelach. Ta klasa oferuje również implementację `IRowsetIdentity`, co pozwala, aby sprawdzić, czy dwa wiersze są takie same. `IRowsetInfo` Interfejsu implementuje właściwości dla obiektu zestawu wierszy. `IConvertType` Interfejs umożliwia dostawcą rozwiązać różnice między typami danych żądanego przez klienta i używanych przez dostawcę.

`IRowset` Interfejsu faktycznie obsługuje pobieranie danych. Konsument najpierw wywołuje metodę o nazwie `GetNextRows` do zwrócenia dojście do wiersza, znane jako `HROW`. Następnie wywołuje konsumenta `IRowset::GetData` z tym `HROW` można pobrać żądanych danych.

`CRowsetImpl` pobiera również kilka parametrów szablonu. Parametry te umożliwiają ustalenie sposobu `CRowsetImpl` klasa służy do obsługi danych. `ArrayType` Argument pozwala określić, jakie mechanizm magazynu jest używane do przechowywania danych wiersza. *RowClass* parametr określa, jakie klasa zawiera `HROW`.

*RowsetInterface* parametr umożliwia również `IRowsetLocate` lub `IRowsetScroll` interfejsu. `IRowsetLocate` i `IRowsetScroll` interfejsy, oba dziedziczyć `IRowset`. W związku z tym szablony dostawców OLE DB należy podać specjalnej obsługi tych interfejsów. Jeśli chcesz użyć jednej z tych interfejsów, należy użyć tego parametru.

## <a name="see-also"></a>Zobacz także

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)<br/>
