---
title: Kreator implementowania interfejsu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.interface.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf2ddf83b7a03f8d4e01b61f82e46e0d26a5547b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33340544"
---
# <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu
Ten kreator implementuje interfejs dla obiekt COM. Implementacje interfejsów wiele znajdują się w bibliotek COM dostępna w programie Visual Studio i systemu Windows. Implementacja interfejsu jest skojarzony z obiektem, gdy tworzone jest wystąpienie tego obiektu i udostępnia usługi, które oferuje obiektu.  
  
 Omówienie implementacji i interfejsów, temacie [interfejsów i implementacje interfejsów](http://msdn.microsoft.com/library/windows/desktop/ms694356) w zestawie Windows SDK.  
  
 **Implementowanie interfejsu**  
 Określa lokalizację biblioteki typów, z którego jest tworzony interfejsu.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Project**|Biblioteka typów jest częścią projektu.|  
|**Registry**|Biblioteka typów jest zarejestrowana w systemie. Zarejestrowanych bibliotek typów są wymienione w **bibliotek typów dostępne**.|  
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