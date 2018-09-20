---
title: Dodawanie klasy (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.adding
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e2ef8ae3e7620efb74099287dcda29210545d2e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420546"
---
# <a name="adding-a-class-visual-c"></a>Dodawanie klasy (Visual C++)

Aby dodać klasę w projekcie w języku Visual C++ w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **klasy**. Spowoduje to otwarcie [klasy okno dialogowe Dodawanie](../ide/add-class-dialog-box.md) okno dialogowe.

Po dodaniu klasy, należy określić nazwę, która różni się od klas, które już istnieją w MFC ani ATL. Jeśli określisz nazwę, która już istnieje w jednej bibliotece IDE Wyświetla informację o błędzie.

Jeśli projekt konwencji nazewnictwa wymaga użycia istniejącej nazwy, możesz po prostu zmienić wielkość liter w co najmniej jedną literę w polu Nazwa ponieważ C++ jest uwzględniana wielkość liter. Na przykład mimo że nie można nadać nazwy klasy `CDocument`, nadaj jej nazwę `cdocument`.

## <a name="what-kind-of-class-do-you-want-to-add"></a>Jakiego rodzaju klasy chcesz dodać?

W **Dodaj klasę** okno dialogowe, po rozwinięciu **Visual C++** węzła w okienku po lewej stronie, wyświetlanych jest kilka grup zainstalowanych szablonów. Są to **CLR**, **ATL**, **MFC**, i **C++**. Po wybraniu grupy, listę dostępnych szablonów w tej grupie jest wyświetlane w środkowym okienku. Każdy szablon zawiera pliki i kod źródłowy, które są wymagane dla klasy.

Aby wygenerować nową klasę, w środkowym okienku wybierz szablon, wpisz nazwę dla klasy w **nazwa** polu, a następnie kliknij przycisk **Dodaj**. Spowoduje to otwarcie **Kreator dodawania klasy** tak, aby określić opcje dla tej klasy.

- Aby uzyskać więcej informacji na temat sposobu tworzenia klas MFC, zobacz [klasy MFC](../mfc/reference/adding-an-mfc-class.md).

- Aby uzyskać więcej informacji na temat tworzenia klasy ATL, zobacz [prosty obiekt ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
>  Szablon **Dodawanie obsługi ATL do MFC** nie tworzy klasę, ale zamiast tego konfiguruje projekt, aby użyć ATL. Aby uzyskać więcej informacji, zobacz [Obsługa ATL w projekcie MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Aby klasy języka C++, która nie używa MFC, ATL lub CLR, użyj **klasy języka C++** szablonu w **C++** grupy zainstalowanych szablonów. Aby uzyskać więcej informacji, zobacz [Dodawanie rodzajowej klasy C++](../ide/adding-a-generic-cpp-class.md).

Dostępne są dwa rodzaje klas C++ opartych na formularzach. Pierwsza z nich, [klasa CFormView](../mfc/reference/cformview-class.md) tworzy klasę MFC. Drugi tworzy klasę CLR Windows Forms.

## <a name="see-also"></a>Zobacz też

[Tworzenie aplikacji MFC opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md)<br>
[Okno dialogowe Dodawanie klasy](../ide/add-class-dialog-box.md)<br>
[Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)