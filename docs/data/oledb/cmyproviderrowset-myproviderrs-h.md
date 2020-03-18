---
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 2c84ff359bdbb39f281928fa0135edd40b1f7d20
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446083"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

Kreator generuje wpis dla obiektu zestawu wierszy. W tym przypadku jest on nazywany `CCustomRowset`. Klasa `CCustomRowset` dziedziczy z klasy dostawcy OLE DB o nazwie `CRowsetImpl`, która implementuje wszystkie niezbędne interfejsy dla obiektu zestawu wierszy. Poniższy kod przedstawia łańcuch dziedziczenia dla `CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass, 
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, 
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` używa również interfejsów `IAccessor` i `IColumnsInfo`. Używa tych interfejsów dla pól danych wyjściowych w tabelach. Klasa zawiera również implementację `IRowsetIdentity`, co umożliwia konsumentowi ustalenie, czy dwa wiersze są takie same. Interfejs `IRowsetInfo` implementuje właściwości dla obiektu zestawu wierszy. Interfejs `IConvertType` umożliwia dostawcy Rozwiązywanie różnic między typami danych żądanymi przez konsumenta a tymi używanymi przez dostawcę.

Interfejs `IRowset` w rzeczywistości obsługuje pobieranie danych. Konsument najpierw wywołuje metodę o nazwie `GetNextRows`, aby zwrócić dojście do wiersza, znane jako `HROW`. Następnie konsument wywoła `IRowset::GetData` z tym `HROW` w celu pobrania żądanych danych.

`CRowsetImpl` również pobiera kilka parametrów szablonu. Te parametry umożliwiają określenie sposobu, w jaki Klasa `CRowsetImpl` obsługuje dane. Argument `ArrayType` pozwala określić, który mechanizm magazynowania jest używany do przechowywania danych wierszy. Parametr *RowClass* określa, jaka klasa zawiera `HROW`.

Parametr *RowsetInterface* umożliwia również korzystanie z interfejsu `IRowsetLocate` lub `IRowsetScroll`. Interfejsy `IRowsetLocate` i `IRowsetScroll` dziedziczą z `IRowset`. W związku z tym szablony dostawcy OLE DB muszą zapewnić specjalną obsługę tych interfejsów. Jeśli chcesz użyć dowolnego z tych interfejsów, musisz użyć tego parametru.

## <a name="see-also"></a>Zobacz też

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)<br/>
