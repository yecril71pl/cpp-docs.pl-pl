---
title: COM + 1.0, Kreator składnika ATL COM + 1.0
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: 0fa649ba41a684be6ed18bd05d48954503c5db16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278595"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM + 1.0, Kreator składnika ATL COM + 1.0

Użyj tej strony, ATL COM + 1.0 składnika kreatora, aby określić typ interfejsu i dodatkowe interfejsy, które są obsługiwane.

Aby uzyskać więcej informacji na temat projektów ATL i klasy ATL COM, zobacz [ATL COM pulpitu składniki](../../atl/atl-com-desktop-components.md).

- **Interface**

   Wskazuje typ interfejsu, który obsługuje obiektu. Domyślnie obiekt obsługuje podwójnego interfejsu.

   |Opcja|Opis|
   |------------|-----------------|
   |**Dual**|Określa, że obiekt obsługuje interfejs podwójny (jego vtable ma niestandardowy interfejs funkcji i późne powiązania `IDispatch` metody). Umożliwia klientom COM i kontrolery automatyzacji dostępu do obiektu.|
   |**Custom**|Określa, że obiekt obsługuje interfejs niestandardowy (jego vtable ma niestandardowy interfejs funkcji). Niestandardowy interfejs może być szybsza niż podwójnego interfejsu, szczególnie w granicach procesu.<br /><br /> - **Automatyzacja zgodne** dodaje obsługę automatyzacji do niestandardowego interfejsu. W przypadku projektów opartego na atrybutach ustawia **oleautomation —** atrybut w klasie coclass.|

- **Kolejkowane**

   Wskazuje, że klientów można wywołać ten składnik asynchronicznie przy użyciu kolejek komunikatów. Dodaje niestandardowy — makro składnika opartego na atrybutach (TLBATTR_QUEUEABLE, 0), plik .h (opartego na atrybutach projektów) lub pliku .idl (nonattributed projektów).

- **Pomoc techniczna**

   Wskazuje, dodatkową obsługę kontroli obiektu i obsługi błędów.

   |Opcja|Opis|
   |------------|-----------------|
   |**Interfejs ISupportErrorInfo**|Tworzy obsługę [Interfejs ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interfejsu, obiekt może zwrócić informacje o błędzie do klienta.|
   |**IObjectControl**|Zapewnia dostęp do tych trzech obiektu [IObjectControl](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectcontrol) metody: [Aktywuj](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled), i [dezaktywować](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate).|
   |**IObjectConstruct**|Tworzy obsługę [IObjectConstruct](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectconstruct) interfejsu, aby zarządzać przekazywanie parametrów przy użyciu innych metod lub obiektów.|

- **Transakcja**

   Wskazuje, że obiekt obsługuje transakcji. Zawiera mtxattr.h pliku w pliku .idl (nonattributed projektów).

   |Opcja|Opis|
   |------------|-----------------|
   |**Obsługiwane**|Określa, że obiekt jest nigdy nie głównego strumienia transakcji, dodając custom(TLBATTR_TRANS_SUPPORTED,0) — makro atrybutu składnika plik .h (opartego na atrybutach projektów) lub pliku .idl (nonattributed projektów).|
   |**Wymagane**|Określa, że obiekt może być, lub może nie być głównego strumienia transakcji, dodając custom(TLBATTR_TRANS_REQUIRED,0) — makro atrybutu składnika plik .h (opartego na atrybutach projektów) lub pliku .idl (nonattributed projektów).|
   |**Nieobsługiwane**|Określa, że obiekt wyklucza transakcji. Plik .h (opartego na atrybutach projektów) lub pliku .idl (nonattributed projektów), dodaje custom(TLBATTR_TRANS_NOTSUPP,0) — makro atrybutu składnika.|
   |**Wymagane nowe**|Określa, że obiekt jest zawsze głównego strumienia transakcji, dodając custom(TLBATTR_TRANS_REQNEW,0) — makro atrybutu składnika plik .h (opartego na atrybutach projektów) lub pliku .idl (nonattributed projektów).|

## <a name="see-also"></a>Zobacz także

[Kreator składników ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[Składnik ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
