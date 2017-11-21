---
title: CMyProviderCommand (MyProviderRS.H) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68846352d3e6b407a4ec7ef6b7993969371a89de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmyprovidercommand-myproviderrsh"></a>CMyProviderCommand (MyProviderRS.H)
`CMyProviderCommand` Klasa jest implementacją dla obiekt polecenia dostawcy. Zapewnia implementację `IAccessor`, `ICommandText`, i **ICommandProperties** interfejsów. `IAccessor` Interfejsu jest taka sama jak w zestawie wierszy. Obiekt polecenia użyto metody dostępu do określenia powiązania parametrów. Obiektu zestawu wierszy używa ich, aby określić powiązania dla kolumny wyjściowe. `ICommandText` Interfejsu jest to wygodny sposób, aby określić polecenie w postaci tekstu. W tym przykładzie użyto `ICommandText` interfejs później, gdy dodaje kod niestandardowy; zastępuje ona również `ICommand::Execute` metody. **ICommandProperties** interfejs obsługuje wszystkie właściwości dla obiektów poleceń i zestawu wierszy.  
  
```  
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
  
 `IAccessor` Interfejsu do zarządzania wszystkimi powiązaniami, które są używane w poleceń i zestawy wierszy. Wywołania konsumenta **IAccessor::CreateAccessor** z tablicą **DBBINDING** struktury. Każdy **DBBINDING** struktura zawiera informacje dotyczące obsługi powiązania kolumny (na przykład typ i długości). Dostawca odbiera struktur i określa, jak powinny być przesyłane dane i określa, czy jakakolwiek są konieczne. `IAccessor` Interfejsu jest używane w obiekcie command do obsługi żadnych parametrów w poleceniu.  
  
 Udostępnia implementację obiektu polecenia `IColumnsInfo`. OLE DB wymaga `IColumnsInfo` interfejsu. Interfejs umożliwia konsumenta można pobrać informacji o parametrach polecenia. Używa obiektu zestawu wierszy `IColumnsInfo` interfejs do zwracania informacji dotyczących kolumn wyjściowych dla dostawcy.  
  
 Dostawca zawiera również interfejs o nazwie `IObjectWithSite`. `IObjectWithSite` Interfejs został wdrożony w ATL 2.0 i umożliwia implementujący w celu przekazywania informacji o sobie do jego podrzędny. Obiekt polecenia używa `IObjectWithSite` informacje, aby sprawdzić wszelkie wygenerowane obiekty zestawu wierszy o który je utworzył.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)