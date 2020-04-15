---
title: Programy obsługi dla standardowych komunikatów systemu Windows
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: 9a136caf3a1d22151cb9cfd48e1cd3f999ab51ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370504"
---
# <a name="handlers-for-standard-windows-messages"></a>Programy obsługi dla standardowych komunikatów systemu Windows

Domyślne programy obsługi standardowych wiadomości systemu Windows (**WM_**) `CWnd`są wstępnie zdefiniowane w klasie . Biblioteka klas opiera nazwy tych programów obsługi na nazwie wiadomości. Na przykład program obsługi wiadomości **WM_PAINT** jest zadeklarowany w: `CWnd`

`afx_msg void OnPaint();`

**Afx_msg** słowo kluczowe sugeruje efekt słowa kluczowego **wirtualnego** języka C++ `CWnd` przez odróżnienie programów obsługi od innych funkcji członkowskich. Należy jednak pamiętać, że te funkcje nie są faktycznie wirtualne; są one zamiast tego implementowane za pośrednictwem map wiadomości. Mapy wiadomości zależą wyłącznie od standardowych makr preprocesora, a nie od żadnych rozszerzeń języka C++. Słowo kluczowe **afx_msg** jest rozpoznawane jako biały znak po wstępnym przetworniu.

Aby zastąpić program obsługi zdefiniowane w klasie podstawowej, po prostu zdefiniuj funkcję z tym samym prototypem w klasie pochodnej i wprowadzić wpis mapy wiadomości dla programu obsługi. Program obsługi "zastępuje" dowolny program obsługi o tej samej nazwie w dowolnej klasie podstawowej.

W niektórych przypadkach program obsługi należy wywołać zastąpionego programu obsługi w klasie podstawowej, więc klasy podstawowej(es) i windows może działać na komunikat. Gdzie można wywołać program obsługi klasy podstawowej w zastąpienia zależy od okoliczności. Czasami należy wywołać program obsługi klasy podstawowej pierwszy i czasami ostatni. Czasami wywołać obsługi klasy podstawowej warunkowo, jeśli zdecydujesz się nie obsługiwać wiadomości samodzielnie. Czasami należy wywołać program obsługi klasy podstawowej, a następnie warunkowo wykonać własny kod obsługi, w zależności od wartości lub stanu zwróconego przez program obsługi klasy podstawowej.

> [!CAUTION]
> Nie jest bezpieczne modyfikowanie argumentów przekazanych do programu obsługi, jeśli zamierzasz przekazać je do programu obsługi klasy podstawowej. Na przykład może być kuszony, aby zmodyfikować `OnChar` *argument nChar* programu obsługi (na przykład przekonwertować na wielkie litery). To zachowanie jest dość niejasne, ale jeśli trzeba osiągnąć `CWnd` ten `SendMessage` efekt, użyj funkcji elementu członkowskiego zamiast tego.

Jak określić prawidłowy sposób zastąpienia danej wiadomości Gdy [Kreator klasy](reference/mfc-class-wizard.md) zapisuje szkielet funkcji obsługi dla `OnCreate` danej wiadomości — program obsługi dla **WM_CREATE**, na przykład — szkicuje w postaci zalecanej funkcji nadrzędnego elementu członkowskiego. W poniższym przykładzie zaleca się, że program obsługi najpierw wywołać program obsługi klasy podstawowej i postępować tylko pod warunkiem, że nie zwraca -1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Zgodnie z konwencją nazwy tych programów obsługi zaczynają się od prefiksu "On". Niektóre z tych programów obsługi nie mają argumentów, podczas gdy inne mają kilka. Niektóre z nich mają również typ zwrotu inny niż **void**. Domyślne programy obsługi dla wszystkich **komunikatów WM_** są dokumentowane w `CWnd` *odwołaniu MFC* jako funkcje członkowskie klasy, których nazwy zaczynają się od "On". Deklaracje funkcji elementu `CWnd` członkowskiego są poprzedzone **afx_msg**.

## <a name="see-also"></a>Zobacz też

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
