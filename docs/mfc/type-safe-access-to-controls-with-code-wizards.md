---
title: Bezpieczny dostęp do formantów z użyciem kreatorów kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f86a8f22bae990261be5150755a26d50d4bef8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950464"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu
Jeśli znasz funkcje DDX, można użyć właściwości formantu w [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) utworzyć bezpieczny dostęp. Ta metoda jest łatwiejsze niż Tworzenie formantów bez użycia kreatorów kodu.  
  
 Jeśli po prostu chcesz uzyskać dostęp do wartości formantu, DDX przekazuje go. Jeśli chcesz przekraczać dostępu wartość formantu umożliwia dodawanie zmiennej członkowskiej klasy odpowiednie do klasy okien dialogowych Kreator dodawania zmiennej elementu członkowskiego. Ta zmienna elementu członkowskiego dołączyć do właściwości formantu.  
  
 Zmienne Członkowskie może mieć właściwości formantu zamiast właściwości Value. Właściwość wartość odwołuje się do typu danych zwróconych z formantu, takie jak `CString` lub **int**. Właściwość formantu umożliwia bezpośredni dostęp do sterowania do elementu członkowskiego danych, którego typ jest jednym z klasy formantów w MFC, takich jak `CButton` lub `CEdit`.  
  
> [!NOTE]
>  W przypadku danego formantu Jeśli chcesz, program może wiele zmiennych Członkowskich z właściwości Value i co najwyżej zmiennej członkowskiej jedną z właściwości formantu. Może mieć tylko jeden obiekt MFC mapowane na formanty, ponieważ wiele obiektów dołączonych do formantu lub dowolnego innego okna może doprowadzić do niejednoznaczności w mapie komunikatów.  
  
 Ten obiekt służy do wywołania funkcji dowolnego elementu członkowskiego dla obiekt formantu. Takie połączenia wpływa na formancie w oknie dialogowym. Na przykład pole wyboru reprezentowane przez zmienną *m_Checkbox*, typu `CButton`, można wywołać:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]  
  
 Tutaj zmiennej członkowskiej *m_Checkbox* pełni tę samą funkcję, jako funkcję elementu członkowskiego `GetMyCheckbox` pokazano [bezpieczny dostęp do formantów bez kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md). Jeśli pole wyboru nie jest pole wyboru automatycznie, będzie nadal potrzebny obsługi w klasy okien dialogowych dla komunikatów powiadomień dotyczących formantu BN_CLICKED po kliknięciu przycisku.  
  
 Aby uzyskać więcej informacji na temat formantów, zobacz [formanty](../mfc/controls-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczny dostęp do formantów w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)   
 [Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md)

