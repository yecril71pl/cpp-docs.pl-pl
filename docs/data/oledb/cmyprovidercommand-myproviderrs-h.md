---
title: CCustomCommand (CustomRS.H) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
- ccustomcommand
- customrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3d3f6b8775ab876834555e7c47e469c72d3a150b
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807736"
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
  
## <a name="see-also"></a>Zobacz też  

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)