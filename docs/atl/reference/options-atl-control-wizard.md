---
title: Opcje, Kreator kontrolki ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 481c97fe7621e9592317f629c2cf87f2f719d5d1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506910"
---
# <a name="options-atl-control-wizard"></a>Opcje, Kreator kontrolki ATL

Ta strona kreatora służy do definiowania typu tworzonego formantu oraz poziomu obsługiwanego przez niego interfejsu.

## <a name="uielement-list"></a>Lista elementów UI

### <a name="control-type"></a>Typ kontrolki

Rodzaj formantu, który ma zostać utworzony.

- **Kontrolka standardowa**: Kontrolka ActiveX.

- **Formant złożony**: Kontrolka ActiveX, która może zawierać (podobnie jak okno dialogowe) inne kontrolki ActiveX lub formanty systemu Windows. Kontrolka złożona obejmuje następujące elementy:

  - Szablon okna dialogowego, który implementuje formant złożony.

  - Zasób niestandardowy, rejestr, który automatycznie rejestruje formant złożony po wywołaniu.

  - Klasa języka C++, która implementuje formant złożony.

  - Interfejs COM uwidoczniony przez formant złożony.

  - Strona testowa HTML zawierająca formant złożony.

    Domyślnie ten formant ustawia [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na true, aby wskazać, że jest to formant okienkowy. Implementuje ona mapę ujścia. Aby uzyskać więcej informacji, zobacz [Obsługa formantów DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Kontrolka DHTML**: formant ATL DHTML określa interfejs użytkownika przy użyciu języka HTML. Klasa interfejsu użytkownika DHTML zawiera mapę COM. Domyślnie ten formant ustawia [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na true, aby wskazać, że jest to formant okienkowy.

   Aby uzyskać więcej informacji, zobacz [Identyfikowanie elementów projektu kontrolki DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Minimalna kontrola

Obsługuje tylko te interfejsy, które są absolutnie niezbędne w większości kontenerów. Można ustawić **minimalną kontrolę** dla dowolnego typu formantu: można utworzyć minimalną kontrolkę Standard, minimalną kontrolkę lub minimalną kontrolkę DHTML.

### <a name="aggregation"></a>Agregacja

Dodaje obsługę agregacji dla tworzonego formantu. Aby uzyskać więcej informacji, zobacz [agregacja](../../atl/aggregation.md).

- **Tak**: Utwórz formant, który może być zagregowany.

- **Nie**: Utwórz formant, którego nie można agregować.

- **Tylko**: Utwórz kontrolkę, którą można utworzyć przy użyciu agregacji.

### <a name="threading-model"></a>Model wątkowości

Określa, że model wątkowości używany przez formant.

- **Single**: formant zostanie uruchomiony tylko w podstawowym wątku com.

- **Apartment**: formant można utworzyć w dowolnym apartamentu pojedynczego wątku. Domyślnie.

### <a name="interface"></a>Interfejs

Typ interfejsu, który ten formant uwidacznia dla kontenera.

- **Dual**: tworzy interfejs, który uwidacznia właściwości i metody za pomocą `IDispatch` i bezpośrednio za pomocą VTBL.

- **Niestandardowy**: tworzy interfejs, który uwidacznia metody bezpośrednio przez VTBL.

   W przypadku wybrania opcji **niestandardowe**można określić, że formant jest **zgodny z automatyzacją**. Jeśli wybierzesz opcję **zgodne z automatyzacją**, Kreator doda atrybut [OleAutomation](../../windows/attributes/oleautomation.md) do interfejsu w IDL, a interfejs może być zorganizowany przez uniwersalnego organizatora w oleaut32.dll. Aby uzyskać więcej informacji, zobacz [organizowanie szczegółów](/windows/win32/com/marshaling-details) w Windows SDK.

   Ponadto, jeśli wybierzesz opcję **zgodne z automatyzacją**, wszystkie parametry dla wszystkich metod w kontrolce muszą być zgodne z wariantem.

### <a name="support"></a>Pomoc techniczna

Ustawia dodatkową pomoc techniczną dla formantu.

- **Punkty połączenia**: włącza punkty połączenia dla obiektu przez uczynienie klasy obiektu pochodną od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) i umożliwienie mu uwidocznienia interfejsu źródłowego.

- **Licencjonowane**: dodaje obsługę kontroli [licencjonowania](/windows/win32/com/licensing). Licencjonowane formanty mogą być obsługiwane tylko wtedy, gdy komputer kliencki ma poprawną licencję.

## <a name="see-also"></a>Zobacz też

[Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md)
