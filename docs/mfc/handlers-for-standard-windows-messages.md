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
ms.openlocfilehash: 4f512c3b9a7fce5cddd582fa774742d2b1ac0967
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907426"
---
# <a name="handlers-for-standard-windows-messages"></a>Programy obsługi dla standardowych komunikatów systemu Windows

Domyślne programy obsługi dla standardowych komunikatów systemu Windows (**WM_** ) są wstępnie zdefiniowane `CWnd`w klasie. Nazwy baz klas dla tych programów obsługi w nazwie komunikatu. Na przykład program obsługi komunikatu **WM_PAINT** jest deklarowany `CWnd` jako:

`afx_msg void OnPaint();`

Słowo kluczowe **afx_msg** sugeruje efekt C++ **wirtualnego** słowa kluczowego poprzez odróżnienie obsługi od innych `CWnd` funkcji Członkowskich. Należy jednak pamiętać, że te funkcje nie są w rzeczywistości wirtualne; Zamiast tego są one wdrażane za poorednictwem map komunikatów. Mapy komunikatów są zależne wyłącznie od standardowych makr preprocesora, a nie na żadnym z C++ rozszerzeń języka. Słowo kluczowe **afx_msg** jest rozpoznawane jako biały znak po przeprowadzeniu wstępnego przetwarzania.

Aby zastąpić procedurę obsługi zdefiniowaną w klasie bazowej, wystarczy zdefiniować funkcję z tym samym prototypem w klasie pochodnej i utworzyć wpis mapy komunikatów dla programu obsługi. Procedura obsługi "przesłania" wszystkie procedury obsługi o tej samej nazwie w dowolnych klasach bazowych klasy.

W niektórych przypadkach procedura obsługi powinna wywołać przesłoniętą procedurę obsługi w klasie bazowej, aby klasy podstawowe i system Windows mogły działać w komunikacie. W przypadku wywołania procedury obsługi klasy podstawowej w zastępowaniu zależą od okoliczności. Czasami należy wywołać procedurę obsługi klasy bazowej jako pierwszą i czasami ostatnią. Czasami wywoływanie warunkowego procedury obsługi klasy podstawowej w przypadku zrezygnowania z obsługi wiadomości. Czasami należy wywołać procedurę obsługi klasy podstawowej, a następnie warunkowo wykonać własny kod procedury obsługi, w zależności od wartości lub stanu zwróconego przez procedurę obsługi klasy podstawowej.

> [!CAUTION]
>  Nie można bezpiecznie modyfikować argumentów przekazywanych do procedury obsługi, jeśli zamierzasz przekazać je do procedury obsługi klasy podstawowej. Na przykład może być skłonny do zmodyfikowania argumentu `OnChar` *nchar* procedury obsługi (na przykład w celu przekonwertowania na wielkie litery). To zachowanie jest dość zasłonięte, ale jeśli chcesz to zrobić, zamiast tego należy użyć `CWnd` funkcji `SendMessage` elementu członkowskiego.

Jak określić właściwy sposób przesłonięcia danego komunikatu, gdy [Kreator klas](reference/mfc-class-wizard.md) zapisuje szkielet funkcji obsługi dla danego komunikatu — `OnCreate` program obsługi **WM_CREATE**, na przykład — szkic w formie zalecanej zastąpiona funkcja członkowska. W poniższym przykładzie zaleca się, aby procedura obsługi najpierw wywołała obsługę klasy podstawowej i kontynuowała tylko wtedy, gdy nie zwraca-1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Według Konwencji nazwy tych programów obsługi zaczynają się prefiksem "on". Niektóre z tych programów obsługi nie przyjmują argumentów, a inne zajmują kilka. Niektóre z nich również mają typ zwracany inny niż **void**. Domyślne programy obsługi dla wszystkich komunikatów **WM_** są udokumentowane w *odwołaniu MFC* jako funkcje elementów członkowskich klasy `CWnd` , których nazwy zaczynają się od "on". Deklaracje funkcji Członkowskich w `CWnd` programie są poprzedzone prefiksem **afx_msg**.

## <a name="see-also"></a>Zobacz także

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
