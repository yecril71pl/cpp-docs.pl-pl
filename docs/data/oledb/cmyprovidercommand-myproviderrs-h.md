---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- ccustomcommand
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: 61bd60b63490303c65729843c3c0351a570a8056
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444150"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

Klasa `CCustomCommand` jest implementacją obiektu polecenia dostawcy. Zawiera implementację interfejsów `IAccessor`, `ICommandText`i `ICommandProperties`. Interfejs `IAccessor` jest taki sam jak w zestawie wierszy. Obiekt Command używa metody dostępu, aby określić powiązania dla parametrów. Obiekt zestawu wierszy używa ich do określania powiązań dla kolumn danych wyjściowych. Interfejs `ICommandText` to przydatny sposób, aby w sposób jednotekstowy określić polecenie. Ten przykład używa interfejsu `ICommandText` w późniejszym czasie, gdy dodaje kod niestandardowy; zastępuje ona również metodę `ICommand::Execute`. Interfejs `ICommandProperties` obsługuje wszystkie właściwości dla obiektów poleceń i zestawów wierszy.

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

Interfejs `IAccessor` zarządza wszystkimi powiązaniami używanymi w poleceniach i zestawach wierszy. Odbiorca wywołuje `IAccessor::CreateAccessor` z tablicą struktur `DBBINDING`. Każda struktura `DBBINDING` zawiera informacje dotyczące sposobu obsługi powiązań kolumn (takich jak typ i długość). Dostawca otrzymuje struktury, a następnie określa, jak powinny być transferowane dane oraz czy są wymagane wszystkie konwersje. Interfejs `IAccessor` jest używany w obiekcie polecenia do obsługi parametrów w poleceniu.

Obiekt Command zawiera również implementację `IColumnsInfo`. OLE DB wymaga interfejsu `IColumnsInfo`. Interfejs umożliwia konsumentowi pobieranie informacji o parametrach z polecenia. Obiekt zestawu wierszy używa interfejsu `IColumnsInfo`, aby zwrócić informacje o kolumnach wyjściowych do dostawcy.

Dostawca zawiera również interfejs o nazwie `IObjectWithSite`. Interfejs `IObjectWithSite` został zaimplementowany w ATL 2,0 i umożliwia programowi implementującemu przekazywanie informacji o sobie bezpośrednio do jego obiektu podrzędnego. Obiekt Command używa informacji `IObjectWithSite` do poinformowania o tym, kto utworzył te obiekty zestawu wierszy.

## <a name="see-also"></a>Zobacz też

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)