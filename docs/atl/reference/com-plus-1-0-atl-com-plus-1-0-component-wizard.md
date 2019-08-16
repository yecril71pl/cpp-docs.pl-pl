---
title: Kreator składnika COM+ 1.0, ATL COM+ 1.0
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: 83b7beafe537f6b271b254d16505b515a41acf27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496693"
---
# <a name="com-10-atl-com-10-component-wizard"></a>Kreator składnika COM+ 1.0, ATL COM+ 1.0

::: moniker range="vs-2019"

Ten Kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ta strona kreatora składnika ATL COM+ 1,0 umożliwia określenie typu interfejsu i dodatkowych interfejsów, które mają być obsługiwane.

Aby uzyskać więcej informacji na temat projektów ATL i klas COM ATL, zobacz [składniki komputerów stacjonarnych ATL com](../../atl/atl-com-desktop-components.md).

- **Interface**

   Wskazuje typ interfejsu obsługiwanego przez obiekt. Domyślnie obiekt obsługuje interfejs podwójny.

   |Opcja|Opis|
   |------------|-----------------|
   |**Dual**|Określa, że obiekt obsługuje podwójny interfejs (jego tablicę zawierającą funkcje interfejsu niestandardowego i metody późnego wiązania `IDispatch` ). Zezwala na dostęp do obiektu zarówno klientom COM, jak i kontrolerom automatyzacji.|
   |**Custom**|Określa, że obiekt obsługuje interfejs niestandardowy (jego tablicę zawierającą niestandardowe funkcje interfejsu). Niestandardowy interfejs może być szybszy niż podwójny interfejs, szczególnie w granicach procesu.<br /><br /> - **Zgodne** z automatyzacją Dodaje obsługę automatyzacji do niestandardowego interfejsu. W przypadku projektów z atrybutami, ustawia atrybut **OleAutomation** w klasie coclass.|

- **Z kolejką**

   Wskazuje, że klienci mogą wywoływać ten składnik asynchronicznie za pomocą kolejek komunikatów. Dodaje niestandardowe makro składnika (TLBATTR_QUEUEABLE, 0) do pliku h (projekty o atrybutach) lub do pliku. idl (projekty nieposiadane).

- **Pomoc techniczna**

   Wskazuje dodatkową pomoc techniczną dla obsługi błędów i kontroli obiektów.

   |Opcja|Opis|
   |------------|-----------------|
   |**ISupportErrorInfo**|Tworzy obsługę interfejsu [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) , aby obiekt mógł zwrócić do klienta informacje o błędzie.|
   |**IObjectControl**|Zapewnia dostęp do trzech metod [IObjectControl](/windows/win32/api/comsvcs/nn-comsvcs-iobjectcontrol) : [Aktywuj](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled)i [Dezaktywuj](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate).|
   |**IObjectConstruct**|Tworzy obsługę interfejsu [IObjectConstruct](/windows/win32/api/comsvcs/nn-comsvcs-iobjectconstruct) , aby zarządzać przekazywaniem parametrów z innych metod lub obiektów.|

- **Transakcja**

   Wskazuje, że obiekt obsługuje transakcje. Obejmuje plik mtxattr. h w pliku IDL (projekty nieposiadane).

   |Opcja|Opis|
   |------------|-----------------|
   |**Obsługiwane**|Określa, że obiekt nigdy nie jest elementem głównym strumienia transakcji, dodając niestandardowe makro atrybutu składnika (TLBATTR_TRANS_SUPPORTED, 0) do pliku h (projekty o atrybutach) lub plik IDL (projekty bez atrybutu).|
   |**Wymagane**|Określa, że obiekt może lub nie jest elementem głównym strumienia transakcji przez dodanie niestandardowego makra atrybutu składnika (TLBATTR_TRANS_REQUIRED, 0) do pliku h (projekty o atrybutach) lub plik IDL (projekty bez atrybutu).|
   |**Nieobsługiwane**|Określa, że obiekt wyklucza transakcje. Dodaje niestandardowe makro atrybutu składnika (TLBATTR_TRANS_NOTSUPP, 0) do pliku h (projekty o atrybutach) lub do pliku IDL (projekty nieposiadane).|
   |**Wymaga nowego**|Określa, że obiekt jest zawsze elementem głównym strumienia transakcji przez dodanie niestandardowego makra atrybutu składnika (TLBATTR_TRANS_REQNEW, 0) do pliku h (projekty o atrybutach) lub plik IDL (projekty nieposiadane).|

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Kreator składników ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[Składnik ATL COM+ 1,0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
