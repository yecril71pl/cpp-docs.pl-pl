---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
- ccustomcommand
- customrs.h
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: b10d7bccae6fa9b86d072b8e13791f23516b2c63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230722"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

`CCustomCommand` Klasa jest implementacją dla obiektu polecenia dostawcy. Zapewnia to implementacja `IAccessor`, `ICommandText`, i `ICommandProperties` interfejsów. `IAccessor` Interfejs jest taka sama jak w zestawie wierszy. Obiekt polecenia używa metody dostępu w celu określenia powiązania parametrów. Obiektu zestawu wierszy są one używane do określenia powiązania dla kolumny wyjściowe. `ICommandText` Interfejsu jest to wygodny sposób, aby określić polecenie w formie tekstu. W tym przykładzie użyto `ICommandText` interfejs później, gdy dodaje niestandardowy kod; zastępuje ona również `ICommand::Execute` metody. `ICommandProperties` Interfejs obsługuje wszystkie właściwości dla obiektów poleceń i wierszy.

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

`IAccessor` Interfejsu zarządza wszystkie powiązania, używany w poleceniach i zestawy wierszy. Wywołania konsumenta `IAccessor::CreateAccessor` z tablicą `DBBINDING` struktury. Każdy `DBBINDING` struktura zawiera informacje dotyczące obsługi powiązania kolumny (takie jak typ i długość). Dostawca otrzymuje struktur i określa, jak należy przenieść dane oraz czy wszystkie konwersje niezbędne. `IAccessor` Interfejs jest używany w obiekcie polecenia do obsługi parametrów w poleceniu.

Obiekt polecenia oferuje również implementację `IColumnsInfo`. OLE DB wymaga `IColumnsInfo` interfejsu. Interfejs umożliwia, aby pobrać informacje o parametrach z polecenia. Używa obiektu zestawu wierszy `IColumnsInfo` interfejsu do zwracania informacji dotyczących kolumn wyjściowych dostawcy.

Dostawca zawiera również interfejs o nazwie `IObjectWithSite`. `IObjectWithSite` Interfejs został wdrożony w wersji 2.0 biblioteki ATL i umożliwia implementujący do przekazywania informacji o sobie samym do jego podrzędny. Obiekt polecenia używa `IObjectWithSite` informacje, aby poinformować dowolne wygenerowane obiekty zestawu wierszy o który je utworzył.

## <a name="see-also"></a>Zobacz także

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)