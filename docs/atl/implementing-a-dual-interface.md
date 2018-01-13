---
title: "Implementującej interfejs podwójną (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae16adcc6743c7e35aae2a4121819a6df50cf4f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-dual-interface"></a>Implementacja interfejsu podwójne
Można zaimplementować interfejs podwójny przy użyciu [elementem IDispatchImpl](../atl/reference/idispatchimpl-class.md) klasy, która udostępnia domyślną implementację elementu `IDispatch` metody w interfejsie podwójny. Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
 Aby użyć tej klasy:  
  
-   Zdefiniuj podwójną interfejsu w bibliotece typów.  
  
-   Pochodną klasy specjalizacji `IDispatchImpl` (przekazują informacje o bibliotece interfejsu i typ jako argumenty szablonu).  
  
-   Dodaj wpis (lub wpisy) do mapy COM do udostępnienia podwójną interfejsu za pomocą `QueryInterface`.  
  
-   Implementuje vtable część interfejsu w klasie.  
  
-   Upewnij się, że biblioteka typów zawierającego definicję interfejsu jest dostępny dla obiektów w czasie wykonywania.  
  
## <a name="atl-simple-object-wizard"></a>Kreator prostych obiektów ATL  
 Jeśli chcesz utworzyć nowy interfejs i nowe klasy do zaimplementowania go, możesz użyć [okno dialogowe Dodawanie klasy ATL](../ide/add-class-dialog-box.md), a następnie [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md).  
  
## <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu  
 Jeśli masz istniejący interfejs, możesz użyć [Kreator implementacji interfejsu](../atl/reference/adding-a-new-interface-in-an-atl-project.md) dodać niezbędne klasy podstawowej, wpisów map COM i implementacje metod szkielet do istniejącej klasy.  
  
> [!NOTE]
>  Może być konieczne dostosowanie wygenerowanej klasy podstawowej, tak aby numery wersji głównej i pomocniczej biblioteki typów są przekazywane jako argumenty szablonu z `IDispatchImpl` klasy podstawowej. Kreator implementacji interfejsu nie Sprawdź numer wersji biblioteki typów.  
  
## <a name="implementing-idispatch"></a>Implementacja interfejsu IDispatch  
 Można użyć `IDispatchImpl` klasy podstawowej na zapewniać implementację elementu dispinterface właśnie, określając odpowiedni wpis w mapie modelu COM (przy użyciu [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) lub [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) makro) zawiera opisujące odpowiedniego interfejsu podwójną biblioteki typów. Dość często, aby zaimplementować `IDispatch` interfejsu na przykład w ten sposób. Kreator prostych obiektów ATL i Kreator interfejsu implementować zarówno założono, że zamierzasz wdrożyć `IDispatch` w ten sposób, więc ich doda odpowiedni wpis do mapy.  
  
> [!NOTE]
>  Oferuje ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) i [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) klas ułatwiająca implementację dispinterfaces bez konieczności biblioteki typów z definicją zgodne interfejs podwójny.  
  
## <a name="see-also"></a>Zobacz też  
 [Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

