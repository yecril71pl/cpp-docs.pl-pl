---
title: Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: b49c1b6f21dfe5270e40649241812320303ad411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370915"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu

Jeśli znasz funkcje DDX, można użyć Control właściwości w [Kreatorze dodawania zmiennych członkowskich,](../ide/add-member-variable-wizard.md) aby utworzyć dostęp bezpieczny dla typu. Takie podejście jest łatwiejsze niż tworzenie formantów bez kreatorów kodu.

Jeśli chcesz po prostu uzyskać dostęp do wartości formantu, DDX zapewnia go. Jeśli chcesz zrobić więcej niż dostęp do wartości formantu, użyj Kreatora dodawania zmiennych elementu członkowskiego, aby dodać zmienną członkowną odpowiedniej klasy do klasy okna dialogowego. Dołącz tę zmienną elementu członkowskiego do control właściwości.

Zmienne członkowskie mogą mieć Control właściwości zamiast Value właściwości. Właściwość wartość odnosi się do typu danych zwróconych `CString` z formantu, takich jak lub **int**. Control Właściwość umożliwia bezpośredni dostęp do formantu za pośrednictwem elementu członkowskiego danych, `CButton` `CEdit`którego typ jest jedną z klas kontroli w MFC, takich jak lub .

> [!NOTE]
> Dla danego formantu, można, jeśli chcesz, mieć wiele zmiennych członkowskich z Value właściwości i co najwyżej jeden zmiennej członkowskiej z Control właściwości. Można mieć tylko jeden obiekt MFC mapowane do formantu, ponieważ wiele obiektów dołączonych do formantu lub innego okna, może prowadzić do niejednoznaczności na mapie wiadomości.

Za pomocą tego obiektu można wywołać dowolne funkcje członkowskie dla obiektu sterującego. Takie wywołania wpływają na formant w oknie dialogowym. Na przykład dla formantu pola wyboru *m_Checkbox*reprezentowanego przez zmienną `CButton`m_Checkbox , typu, można wywołać:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

W tym miejscu zmienna elementu członkowskiego *m_Checkbox* służy `GetMyCheckbox` temu samejednecji, co funkcja elementu członkowskiego pokazana w [kreatorze bezpiecznego dostępu do kontrolek bez kodu.](../mfc/type-safe-access-to-controls-without-code-wizards.md) Jeśli pole wyboru nie jest automatyczne pole wyboru, nadal trzeba obsługi w klasie okna dialogowego dla BN_CLICKED komunikat z powiadomieniem o kontroli po kliknięciu przycisku.

Aby uzyskać więcej informacji na temat formantów, zobacz [Formanty](../mfc/controls-mfc.md).

## <a name="see-also"></a>Zobacz też

[Bezpieczny dostęp do kontrolek w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Praca z oknami dialogowymi w MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md)
