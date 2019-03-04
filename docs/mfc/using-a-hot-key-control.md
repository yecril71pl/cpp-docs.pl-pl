---
title: Używanie formantu klawisza dostępu
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
ms.openlocfilehash: d9178fe989e476111a3da55861642e9aa6311872
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260585"
---
# <a name="using-a-hot-key-control"></a>Używanie formantu klawisza dostępu

Typowe użycie formantu klawisza dostępu jest zgodny ze wzorcem poniżej:

- Formant zostanie utworzony. Kontrolka została określona w szablonu okna dialogowego, tworzenie przebiega automatycznie podczas tworzenia okna dialogowego. (Powinien mieć [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) elementu członkowskiego w swojej klasie okna dialogowego, która odnosi się do formantu klawisza dostępu.) Alternatywnie, można użyć [Utwórz](../mfc/reference/chotkeyctrl-class.md#create) funkcja elementu członkowskiego, aby utworzyć formant jako okna podrzędnego każdego okna.

- Jeśli chcesz ustawić wartość domyślną dla formantu, wywołaj [SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) funkcja elementu członkowskiego. Jeśli chcesz zabronić określone stany shift, wywołaj [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). W przypadku kontrolek w oknie dialogowym jest odpowiedni moment, aby to zrobić, w oknie dialogowym [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji.

- Użytkownik wchodzi w interakcję z kontrolką naciskając kombinację klawiszy dostępu, po aktywowaniu formantu klawisza dostępu. Użytkownik następnie jakiś sposób wskazuje, że to zadanie jest zakończone, być może, klikając przycisk w oknie dialogowym.

- Gdy program jest powiadamiany o to, że użytkownik wybrał klawisza dostępu, powinna korzystać funkcja elementu członkowskiego [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) można pobrać wartości wirtualnego stanu key- and -shift z formantu klawisza dostępu.

- Jeśli znasz już klucza co wybrany przez użytkownika, można ustawić klawisza dostępu przy użyciu jednej z metod opisanych w [Ustawianie klawisza dostępu](../mfc/setting-a-hot-key.md).

- Jeśli formantu klawisza dostępu znajduje się w oknie dialogowym go i `CHotKeyCtrl` obiekt jest niszczony automatycznie. Jeśli nie, musisz upewnij się, że obie kontrolki i `CHotKeyCtrl` obiektu są poprawnie niszczone.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
