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
ms.openlocfilehash: d60ae52225ddd993c1768d0b5ce1989ab0192e45
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275392"
---
# <a name="handlers-for-standard-windows-messages"></a>Programy obsługi dla standardowych komunikatów systemu Windows

Domyślne programy obsługi dla standardowych komunikatów Windows (**WM_**) są wstępnie zdefiniowane w klasie `CWnd`. Biblioteka klas określa nazwy dla tych programów obsługi na Nazwa komunikatu. Na przykład program obsługi dla **WM_PAINT** wiadomości jest zadeklarowana w `CWnd` jako:

`afx_msg void OnPaint();`

**Afx_msg** — słowo kluczowe sugeruje efekt C++ **wirtualnego** — słowo kluczowe przy rozróżnianiu obsługi z innych `CWnd` funkcji elementów członkowskich. Należy jednak pamiętać, że te funkcje nie są w rzeczywistości wirtualnej; Zamiast tego są one wykonywane za pomocą mapy komunikatów. Mapy komunikatów zależą od wyłącznie standardowe makra preprocesora, nie na jakichkolwiek rozszerzeń języka C++. **Afx_msg** — słowo kluczowe jest rozpoznawana jako biały znak po przetwarzania wstępnego.

Aby zastąpić procedurę obsługi zdefiniowaną w klasie bazowej, po prostu zdefiniuj funkcję z tego samego prototypu w klasie pochodnej i nawiązać wpis mapy komunikatów dla programu obsługi. Programu obsługi "zastępuje" każdy program obsługi o takiej samej nazwie w jednym z klasy bazowe tej klasy.

W niektórych przypadkach programu obsługi należy wywołać obsługi zastąpione w klasie bazowej tak klas podstawowych i Windows, które mogą działać w komunikacie. Gdy wywołujesz obsługi klasa bazowa przesłonięcia zależy od okoliczności. Czasami, należy najpierw wywołać procedurę obsługi klasy podstawowej i czasem ostatniego. Czasami możesz wywołać program obsługi klasy bazowej warunkowo, jeśli nie zdecydujesz się na siebie obsłużyć komunikat. Czasami możesz powinien wywoływanie programu do obsługi klasy bazowej, a następnie warunkowo wykonywanie własnego kodu programu obsługi, w zależności od wartości lub stan zwrócone przez procedurę obsługi klasy bazowej.

> [!CAUTION]
>  Nie jest bezpieczne argumenty przekazywane do programu obsługi, jeśli zamierzasz przekazać ich do obsługi klasy bazowej. Na przykład, być może uznasz, że aby zmodyfikować *nChar* argument `OnChar` obsługi (do przekonwertowania na wielkie litery, na przykład). To zachowanie jest dość zasłoniętej, ale jeśli potrzebujesz osiągnąć ten efekt `CWnd` funkcja elementu członkowskiego `SendMessage` zamiast tego.

Jak określić prawidłowego sposobu zastąpienia danej komunikatów, gdy w oknie właściwości zapisuje szkielet funkcji obsługi dla danego komunikatu — `OnCreate` Obsługa **WM_CREATE**, na przykład — szkice go w formie Funkcja zalecane zgodnym z przesłoniętą składową. Poniższy przykład zaleca obsługi najpierw wywoływanie programu do obsługi klasy podstawowej i kontynuować tylko pod warunkiem, że nie zwraca -1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Według Konwencji nazwy te programy obsługi zaczynają się od prefiksu "On". Niektóre z tych programów obsługi nie przyjmują argumentów, podczas gdy inne przejąć kilka. Niektóre również mieć zwracanego typu innego niż **void**. Programy obsługi domyślnego dla wszystkich **WM_** komunikaty są udokumentowane w *odwołanie MFC* jako funkcje Członkowskie klasy `CWnd` których nazwy zaczynają się od "On". W deklaracjach funkcji Członkowskich `CWnd` mają prefiks **afx_msg**.

## <a name="see-also"></a>Zobacz także

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
