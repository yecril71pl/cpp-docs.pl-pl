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
ms.openlocfilehash: 100b792750c0534d0b4e0b69c4acfd349e5897ed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442327"
---
# <a name="implement-interface-wizard"></a>Kreator implementacji interfejsu

Ten kreator implementuje interfejs dla obiektu COM. Implementacje wiele interfejsów są objęte biblioteki COM, dostępna z poziomu programu Visual Studio i Windows. Implementacja interfejsu jest skojarzony z obiektem, gdy tworzone jest wystąpienie tego obiektu i udostępnia usługi, które są oferowane na obiekt.

Omówienie interfejsów i implementacji, zobacz [interfejsów i implementacje interfejsu](/windows/desktop/com/interfaces-and-interface-implementations) w zestawie Windows SDK.

- **Implementuj interfejs z**

   Określa lokalizację biblioteki typów, z którego jest tworzony interfejs.

   |Opcja|Opis|
   |------------|-----------------|
   |**Project**|Biblioteka typów jest częścią projektu.|
   |**Registry**|Biblioteka typów jest zarejestrowany w systemie. Zarejestrowanego typu biblioteki są wymienione w **bibliotek typów dostępnych**.|
   |**Plik**|Biblioteka typów nie zawsze jest zarejestrowany w systemie, ale jest zawarty w pliku. Należy podać lokalizację pliku w **lokalizacji**.|

- **Biblioteki typów dostępne**

   Wyświetla bibliotek dostępnych typów zawierający definicje interfejsu, które można zaimplementować. Jeśli klikniesz **pliku** w obszarze **implementuj interfejs z**, to pole jest niedostępna w przypadku zmiany.

- **Lokalizacja**

   Wyświetla lokalizację biblioteki typów, aktualnie wybrane w **bibliotek typów dostępnych** listy. W przypadku wybrania **pliku** w obszarze **implementuj interfejs z**, kliknij przycisk wielokropka, aby zlokalizować pliku zawierającego bibliotekę typów, aby użyć.

- **Interfejsy**

   Wyświetla interfejsy, których definicje znajdują się w aktualnie wybranego w bibliotece typów **bibliotek typów dostępnych** pole.

   > [!NOTE]
   > Interfejsy, które mają taką samą nazwę jak już wdrożone przez wybrany obiekt nie są wyświetlane w **interfejsów** pole.

   |Przycisk transferu|Opis|
   |---------------------|-----------------|
   |**>**|Dodaje do **implementować interfejsy** Nazwa interfejsu, aktualnie wybrane w listy **interfejsów** listy.|
   |**>>**|Dodaje do **implementować interfejsy** listy dostępny w wszystkich nazw interfejsu **interfejsów** listy.|
   |**\<**|Usuwa nazwę interfejsu aktualnie wybrany w **implementować interfejsy** listy.|
   |**\<\<**|Usuwa wszystkie interfejsu nazwy obecnie wymienione w **implementować interfejsy** listy.|

- **Implementowanie interfejsów**

   Wyświetla nazwy interfejsów, które zostały wybrane do wdrożenia na obiekcie.

   > [!NOTE]
   > Jeśli dołączysz więcej niż jeden interfejs, który pochodzi od klasy `IDispatch`, lub jeśli użytkownik próbuje zaimplementować interfejs, który jest tworzony na podstawie innego interfejsu już w swojej klasie, a następnie muszą rozróżniać wpisy COM_MAP. Zobacz [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md)