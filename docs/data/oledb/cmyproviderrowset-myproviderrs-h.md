---
title: CMyProviderRowset (MyProviderRS.H) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e8a099ed08075877b7ca611e15994c2d68c25137
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)
Kreator generuje wpis dla obiektu zestawu wierszy. W tym przypadku jest to `CMyProviderRowset`. `CMyProviderRowset` Klasa dziedziczy z klasy dostawcy OLE DB o nazwie `CRowsetImpl`, który implementuje interfejsów wymaganych dla obiektu zestawu wierszy. Poniższy kod przedstawia łańcuch dziedziczenia dla `CRowsetImpl`:  
  
```  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T > >  
```  
  
 `CRowsetImpl`używa również `IAccessor` i `IColumnsInfo` interfejsów. Używa tych interfejsów dla pól danych wyjściowych w tabelach. Udostępnia implementację klasy **IRowsetIdentity**, dzięki czemu konsumentów do ustalenia, czy dwa wiersze są identyczne. `IRowsetInfo` Interfejsu implementuje właściwości dla obiektu zestawu wierszy. **IConvertType** interfejs umożliwia dostawcy Rozwiąż problemy dotyczące różnic między typami danych żądanej przez klienta i używanych przez dostawcę.  
  
 `IRowset` Interfejsu faktycznie obsługuje pobierania danych. Konsument najpierw wywołuje metodę o nazwie `GetNextRows` do zwrócenia dojściem do wiersza, znany jako **HROW**. Następnie wywołuje konsumenta **IRowset::GetData** z tym **HROW** można pobrać żądanych danych.  
  
 `CRowsetImpl`ma również kilka parametrów szablonu. Parametry te umożliwiają ustalenie sposobu `CRowsetImpl` klasy obsługi danych. `ArrayType` Argument pozwala określić, jakie mechanizmu magazynowania jest używany do przechowywania danych wiersza. **RowClass** parametr określa, jakie klasa zawiera **HROW**.  
  
 **RowsetInterface** parametr umożliwia także użycie `IRowsetLocate` lub `IRowsetScroll` interfejsu. `IRowsetLocate` i `IRowsetScroll` interfejsy zarówno dziedziczyć `IRowset`. W związku z tym szablony dostawców OLE DB musi podać specjalnej obsługi dla tych interfejsów. Jeśli chcesz użyć dowolnej z tych interfejsów, należy użyć tego parametru.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)