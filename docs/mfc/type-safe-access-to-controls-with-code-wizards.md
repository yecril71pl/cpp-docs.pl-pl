---
title: Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: 5f0bf03adff83ef25f3537291516368151a31a03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436295"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu

Jeśli znasz funkcje DDX, można użyć właściwości formantu w [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) Aby utworzyć bezpieczny dostęp. To podejście jest prostsze niż tworzenie kontrolek bez użycia kreatorów kodu.

Jeśli po prostu chcesz mieć dostęp do wartości kontrolki, DDX dostarcza mu. Jeśli chcesz więcej niż dostęp do wartości kontrolki, należy użyć Kreator dodawania zmiennej składowej do dodawania zmiennej członkowskiej odpowiedniej klasy do klasy okien dialogowych. Ta zmienna członka należy dołączyć do właściwości kontrolki.

Zmienne Członkowskie może mieć właściwości kontrolki, a nie właściwości Value. Wartość właściwości odwołuje się do typu danych zwracanych z kontrolki, takie jak `CString` lub **int**. Właściwości kontrolki umożliwia bezpośredni dostęp do formantu za pomocą element członkowski danych, którego typ jest jednym z klasy kontrolek w MFC, takich jak `CButton` lub `CEdit`.

> [!NOTE]
>  Dla danej kontrolki Jeśli chcesz, masz wiele zmiennych Członkowskich z tych właściwości Value i co najwyżej jeden element członkowski zmiennej z właściwością kontrolki. Może mieć tylko jeden obiekt MFC zamapowane na kontrolkę, ponieważ wiele obiektów dołączonych do kontrolkę lub inne okno, co może spowodować niejednoznaczność w mapie wiadomości.

Ten obiekt jest używany do wywołania dowolnego elementu członkowskiego funkcji dla obiektu formantu. Takie połączenia wpływa na kontrolki w oknie dialogowym. Na przykład pole wyboru, formantu reprezentowane za pomocą zmiennej *m_Checkbox*, typu `CButton`, można wywołać:

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Tutaj zmiennej składowej *m_Checkbox* pełni tę samą funkcję, jako funkcję składową `GetMyCheckbox` objętego [bezpieczny dostęp do kontrolek bez kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md). Jeśli pole wyboru nie jest pole wyboru automatycznie, będzie nadal konieczne program obsługi w klasy okien dialogowych dla komunikatu powiadamianie kontrolki BN_CLICKED po kliknięciu przycisku.

Aby uzyskać więcej informacji na temat formantów, zobacz [formantów](../mfc/controls-mfc.md).

## <a name="see-also"></a>Zobacz też

[Bezpieczny dostęp do kontrolek w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md)

