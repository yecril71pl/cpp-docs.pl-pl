---
title: CMyProviderCommand (MyProviderRS.H) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b437f02a0df4f4ff0e34c44939c2a40f3ccebf74
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339744"
---
# <a name="cmyprovidercommand-myproviderrsh"></a>CMyProviderCommand (MyProviderRS.H)
`CMyProviderCommand` Klasa jest implementacją dla obiektu polecenia dostawcy. Zapewnia to implementacja `IAccessor`, `ICommandText`, i `ICommandProperties` interfejsów. `IAccessor` Interfejs jest taka sama jak w zestawie wierszy. Obiekt polecenia używa metody dostępu w celu określenia powiązania parametrów. Obiektu zestawu wierszy są one używane do określenia powiązania dla kolumny wyjściowe. `ICommandText` Interfejsu jest to wygodny sposób, aby określić polecenie w formie tekstu. W tym przykładzie użyto `ICommandText` interfejs później, gdy dodaje niestandardowy kod; zastępuje ona również `ICommand::Execute` metody. `ICommandProperties` Interfejs obsługuje wszystkie właściwości dla obiektów poleceń i wierszy.  
  
```cpp  
// CMyProviderCommand  
class ATL_NO_VTABLE CMyProviderCommand :   
class ATL_NO_VTABLE CMyProviderCommand :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IAccessorImpl<CMyProviderCommand>,  
   public ICommandTextImpl<CMyProviderCommand>,  
   public ICommandPropertiesImpl<CMyProviderCommand>,  
   public IObjectWithSiteImpl<CMyProviderCommand>,  
   public IConvertTypeImpl<CMyProviderCommand>,  
   public IColumnsInfoImpl<CMyProviderCommand>  
```  
  
 `IAccessor` Interfejsu zarządza wszystkie powiązania, używany w poleceniach i zestawy wierszy. Wywołania konsumenta `IAccessor::CreateAccessor` z tablicą `DBBINDING` struktury. Każdy `DBBINDING` struktura zawiera informacje dotyczące obsługi powiązania kolumny (takie jak typ i długość). Dostawca otrzymuje struktur i określa, jak należy przenieść dane oraz czy wszystkie konwersje niezbędne. `IAccessor` Interfejs jest używany w obiekcie polecenia do obsługi parametrów w poleceniu.  
  
 Obiekt polecenia oferuje również implementację `IColumnsInfo`. OLE DB wymaga `IColumnsInfo` interfejsu. Interfejs umożliwia, aby pobrać informacje o parametrach z polecenia. Używa obiektu zestawu wierszy `IColumnsInfo` interfejsu do zwracania informacji dotyczących kolumn wyjściowych dostawcy.  
  
 Dostawca zawiera również interfejs o nazwie `IObjectWithSite`. `IObjectWithSite` Interfejs został wdrożony w wersji 2.0 biblioteki ATL i umożliwia implementujący do przekazywania informacji o sobie samym do jego podrzędny. Obiekt polecenia używa `IObjectWithSite` informacje, aby poinformować dowolne wygenerowane obiekty zestawu wierszy o który je utworzył.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)