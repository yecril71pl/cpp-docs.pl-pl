---
title: Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: fefa722209d37e2612201c4471e5764f9d71f27a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685035"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu

Jeśli znasz funkcje DDX, możesz użyć właściwości kontrolki w [Kreatorze dodawania zmiennej członkowskiej](../ide/add-member-variable-wizard.md) , aby utworzyć bezpieczny dostęp do typu. Takie podejście jest łatwiejsze niż Tworzenie kontrolek bez użycia kreatorów kodu.

Jeśli chcesz po prostu uzyskać dostęp do wartości kontrolki, DDX udostępnia ją. Jeśli chcesz uzyskać więcej niż dostęp do wartości kontrolki, użyj Kreatora dodawania zmiennej składowej, aby dodać zmienną członkowską odpowiedniej klasy do klasy okna dialogowego. Dołącz tę zmienną członkowską do właściwości Control.

Zmienne składowe mogą mieć właściwość kontrolki zamiast właściwości Value. Właściwość Value odwołuje się do typu danych zwracanych z kontrolki, takich jak `CString` lub **int**. Właściwość kontrolki umożliwia bezpośredni dostęp do kontrolki za pośrednictwem elementu członkowskiego danych, którego typ jest jednym z klas formantów w MFC, takich jak `CButton` lub `CEdit`.

> [!NOTE]
>  W przypadku danej kontrolki można, jeśli chcesz, mieć wiele zmiennych składowych z właściwością Value i co najwyżej jedną zmienną członkowską z właściwością Control. Do kontrolki można zamapować tylko jeden obiekt MFC, ponieważ wiele obiektów dołączonych do kontrolki lub dowolnego innego okna prowadziłoby do niejednoznaczności mapy komunikatów.

Można użyć tego obiektu do wywołania wszelkich funkcji Członkowskich dla obiektu Control. Takie wywołania mają wpływ na kontrolkę w oknie dialogowym. Na przykład dla kontrolki pole wyboru reprezentowanej przez zmienną *m_Checkbox*typu `CButton` można wywołać:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

W tym miejscu zmienna członkowska *m_Checkbox* służy do tego samego celu co funkcja członkowska `GetMyCheckbox` pokazana w [bezpiecznym typie dostęp do formantów bez kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md). Jeśli pole wyboru nie jest polem wyboru, w klasie okna dialogowego nadal będzie potrzebna procedura obsługi dla komunikatu BN_CLICKED Control — powiadomienie, gdy przycisk zostanie kliknięty.

Aby uzyskać więcej informacji na temat kontrolek, zobacz [Controls](../mfc/controls-mfc.md).

## <a name="see-also"></a>Zobacz także

[Bezpieczny dostęp do kontrolek w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md)
