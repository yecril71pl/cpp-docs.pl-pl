---
title: Opcje, Kreator kontrolki ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 1dd136739162c72d8064deb9b1498794f1985e1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197357"
---
# <a name="options-atl-control-wizard"></a>Opcje, Kreator kontrolki ATL

Ta strona kreatora służy do definiowania typu formantu, który tworzysz, i zawiera poziom obsługi interfejsu.

## <a name="uielement-list"></a>Lista elementów UI

### <a name="control-type"></a>Typ formantu

Rodzaj kontrolki, którą chcesz utworzyć.

- **Formantu standardowego**: Kontrolki ActiveX.

- **Kontrolki złożonej**: Formant ActiveX, który może zawierać (podobnie do okna dialogowego) innych formantów ActiveX lub formanty Windows. Kontrolki złożonej obejmuje następujące funkcje:

  - Szablon dla okna dialogowego, który implementuje złożonego formantu.

  - Zasób niestandardowy, rejestru, co powoduje automatyczne zarejestrowanie złożonego formantu po wywołaniu.

  - Klasy języka C++, który implementuje złożonego formantu.

  - Interfejs COM udostępnianych przez złożonego formantu.

  - Testową stronę HTML zawierający złożonego formantu.

    Domyślnie ten formant ustawia [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na wartość true, aby wskazać, że jest to okna formantu. Implementuje mapę ujścia. Aby uzyskać więcej informacji, zobacz [obsługę kontrolki DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Kontrolki DHTML**: Kontrolki ATL DHTML określa interfejs użytkownika, za pomocą kodu HTML. Klasa interfejsu użytkownika DHTML zawiera mapę COM. Domyślnie ten formant ustawia [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na wartość true, aby wskazać, że jest to okna formantu.

   Aby uzyskać więcej informacji, zobacz [identyfikowanie elementów projektu kontrolki DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Kontrolka minimalnego

Obsługuje tylko interfejsy, które są całkowicie wymagane przez większość kontenerów. Możesz ustawić **kontrolka minimalnego** dla każdego z typów kontroli: można utworzyć kontrolki standardowej minimalny, formantu złożonego minimalnego lub minimalnego kontrolki DHTML.

### <a name="aggregation"></a>Agregacji

Dodaje obsługę agregacji dla formantu, który tworzysz. Aby uzyskać więcej informacji, zobacz [agregacji](../../atl/aggregation.md).

- **Tak**: Utwórz formant, który może być agregowany.

- **Nie**: Utwórz formant, który nie można agregować.

- **Only**: Utwórz formant, który może być tylko utworzone za pomocą agregacji.

### <a name="threading-model"></a>Model wątkowości

Określa, że model wątkowości używany przez kontrolkę.

- **Pojedynczy**: Kontrolka będzie uruchamiane tylko w podstawowym wątku com.

- **Apartamentu**: Kontrolki można utworzyć w dowolnym komórka wątku pojedynczego. Domyślnie.

### <a name="interface"></a>Interface

Typ interfejsu, który udostępnia tę kontrolkę, do kontenera.

- **Podwójna**: Tworzy interfejs, który udostępnia właściwości i metod za pośrednictwem `IDispatch` oraz bezpośrednio z poziomu VTBL.

- **Niestandardowe**: Tworzy interfejs, który udostępnia metody bezpośrednio za pomocą VTBL.

   Jeśli wybierzesz **niestandardowe**, możesz określić, czy kontrolka jest **zgodnego z automatyzacji**. Po wybraniu **zgodnego z automatyzacji**, wówczas Kreator dodaje [oleautomation —](../../windows/oleautomation.md) atrybut interfejsu w pliku IDL, i interfejs mogą być organizowane przez organizatora uniwersalnych w oleaut32.dll. Zobacz [Marshaling szczegóły](/windows/desktop/com/marshaling-details) w zestawie Windows SDK, aby uzyskać więcej informacji.

   Ponadto jeśli wybierzesz **zgodnego z automatyzacji**, wszystkie parametry dla wszystkich metod w kontrolce musi być typ VARIANT zgodne.

### <a name="support"></a>Pomoc techniczna

Ustawia różne obsługę formantu.

- **Punkty połączenia**: Włącza punkty połączenia dla obiektu, wprowadzając nazwę obiektu klasy pochodzi od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) , dzięki czemu go do udostępnienia interfejs źródłowy.

- **Licencjonowane**: Dodaje obsługę do formantu dla [licencjonowania](/windows/desktop/com/licensing). Licencjonowane formanty mogą być hostowane tylko, jeśli komputer kliencki ma odpowiednią licencję.

## <a name="see-also"></a>Zobacz także

[Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md)
