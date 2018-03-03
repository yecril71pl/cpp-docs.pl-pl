---
title: Kreator implementowania interfejsu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.impl.interface.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d224546eb8bb06421c2e84206e1f4d4dc77f9668
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu
Ten kreator implementuje interfejs dla obiekt COM. Implementacje interfejsów wiele znajdują się w bibliotek COM dostępna w programie Visual Studio i systemu Windows. Implementacja interfejsu jest skojarzony z obiektem, gdy tworzone jest wystąpienie tego obiektu i udostępnia usługi, które oferuje obiektu.  
  
 Omówienie implementacji i interfejsów, temacie [interfejsów i implementacje interfejsów](http://msdn.microsoft.com/library/windows/desktop/ms694356) w zestawie Windows SDK.  
  
 **Implementowanie interfejsu**  
 Określa lokalizację biblioteki typów, z którego jest tworzony interfejsu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Projekt**|Biblioteka typów jest częścią projektu.|  
|**Rejestru**|Biblioteka typów jest zarejestrowana w systemie. Zarejestrowanych bibliotek typów są wymienione w **bibliotek typów dostępne**.|  
|**Plik**|Biblioteki typów nie zawsze jest zarejestrowany w systemie, ale jest zawarty w pliku. Należy podać lokalizację pliku w **lokalizacji**.|  
  
 **Biblioteki typów dostępne**  
 Wyświetla dostępne type libraries definicjami interfejsu, które można wdrożyć. Jeśli klikniesz przycisk **pliku** w obszarze **implementuj interfejs z**, to pole jest niedostępna w przypadku zmiany.  
  
 **Lokalizacja**  
 Wyświetla lokalizację biblioteki typów aktualnie wybrane w **bibliotek typów dostępne** listy. W przypadku wybrania **pliku** w obszarze **implementuj interfejs z**, kliknij przycisk wielokropka, aby zlokalizować plik zawierający typ bibliotekę do użycia.  
  
 **Interfejsy**  
 Wyświetla interfejsy, w których definicje znajdują się w bibliotece typów aktualnie wybrane w **bibliotek typów dostępne** pole.  
  
> [!NOTE]
>  Interfejsy, które mają taką samą nazwę jak już wdrożone przez wybrany obiekt nie są wyświetlane w **interfejsów** pole.  
  
|Przycisk transferu|Opis|  
|---------------------|-----------------|  
|**>**|Dodaje do **implementować interfejsów** listy z nazwą interfejsu aktualnie wybrane w **interfejsów** listy.|  
|**>>**|Dodaje do **implementować interfejsów** listę wszystkich nazw interfejsu dostępne w **interfejsów** listy.|  
|**<**|Usuwa nazwę interfejsu aktualnie wybrane w **implementować interfejsów** listy.|  
|**<\<**|Usuwa wszystkie interfejsu nazw znajdujących się na liście w **implementować interfejsów** listy.|  
  
 **Implementowanie interfejsów**  
 Wyświetla nazwy interfejsów, które zostały wybrane do wdrożenia na obiekt.  
  
> [!NOTE]
>  Jeśli dołączysz więcej niż jeden interfejs, która jest pochodną `IDispatch`, lub jeśli użytkownik próbuje zaimplementować interfejs, który pochodzi z innego interfejsu już w klasie, a następnie należy usunąć niejednoznaczność wpisy COM_MAP. Zobacz [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md)