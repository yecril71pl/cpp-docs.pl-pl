---
title: Alternatywy dla architektury dokumentu widoku
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 98bb4de2f6d1a43fc1958a0fcbaafa1ac0af82a3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282555"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternatywy dla architektury dokument/widok

Aplikacje MFC zwykle korzystają architektury dokument/widok do zarządzania informacjami, formaty plików i wizualna reprezentacja danych dla użytkowników. Dla większości aplikacji klasycznych architektury dokument/widok to Architektura aplikacji odpowiednie i efektywne. Ta architektura oddziela dane z przeglądania i w większości przypadków, upraszcza aplikacji i zmniejsza nadmiarowy kod.

Jednak architektury dokument/widok nie jest odpowiednie w niektórych sytuacjach. Należy wziąć pod uwagę te przykłady:

- Czy przenoszenie aplikacji napisanych w języku C dla Windows, można wykonać portów przed dodaniem dokument/widok pomocy technicznej do Twojej aplikacji.

- Jeśli piszesz uproszczone narzędzia możesz znaleźć, co można zrobić bez architektury dokument/widok.

- Jeśli oryginalny kod już napisana zarządzanie danymi przy użyciu danych wyświetlania, przenoszenie kodu do modelu dokumentu/widoku nie jest warte włożonej pracy, ponieważ muszą być rozdzielone dwa. Warto pozostawić kod jest.

Aby utworzyć aplikację, która nie korzysta z architektury dokument/widok, wyczyść **Obsługa architektury dokument/widok** pole wyboru w kroku 1 procedury Kreator aplikacji MFC. Zobacz [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) Aby uzyskać szczegółowe informacje.

> [!NOTE]
>  Oparta na oknach dialogowych aplikacji utworzone przez Kreatora aplikacji MFC nie należy używać architektury dokument/widok, więc **Obsługa architektury dokument/widok** pole wyboru jest wyłączone, jeśli typ aplikacji okna dialogowego.

Kreatorów Visual C++, a także Edytory źródłowe i okna dialogowego, pracować z wygenerowanej aplikacji, tak samo, jak za pomocą dowolnej generowane przez Kreatora aplikacji. Aplikacja może obsługiwać paski narzędzi, paski przewijania i pasek stanu i ma **o** pole. Aplikacja nie zarejestruje żadnych szablonów dokumentów i nie będzie zawierać klasy dokumentu.

Należy pamiętać, że wygenerowanej aplikacji ma klasę widoku `CChildView`, pochodzącej z `CWnd`. MFC tworzy i umieszcza jedno wystąpienie klasy widoku w ramach okien ramowych tworzone przez testowaną aplikację. MFC nadal wymusza korzystanie z okna widoku, ponieważ upraszcza rozmieszczania i zarządzania zawartością aplikacji. Można dodać kod rysowania `OnPaint` elementu członkowskiego tej klasy. Kod należy dodać paski przewijania, do widoku, a nie do ramki.

Ponieważ architektury dokument/widok dostarczonych przez MFC jest odpowiedzialny za realizację wielu podstawowych funkcji aplikacji, jego nieobecności w projekcie oznacza, że jesteś odpowiedzialny za realizację wielu ważnych funkcji aplikacji:

- Zgodnie z postanowieniami przez Kreatora aplikacji MFC, menu aplikacji zawiera tylko **New** i **zakończenia** polecenia na **pliku** menu. ( **New** polecenie jest obsługiwane tylko dla aplikacji MDI, obsługa nie aplikacje SDI bez dokument/widok.) Resource wygenerowany menu nie obsługuje listy ostatnio używanych elementów (ostatnio używane).

- Należy dodać funkcje obsługi i implementacje dla dowolnego polecenia, które będzie obsługiwać aplikacji, w tym **Otwórz** i **Zapisz** na **pliku** menu. MFC zwykle zapewnia kodu do obsługi tych funkcji, ale obsługa jest ściśle powiązany z architektury dokumentu/widoku.

- Pasek narzędzi dla aplikacji, żądanie będzie minimalny.

Zdecydowanie zaleca się użyć Kreatora aplikacji MFC do tworzenia aplikacji bez architektury dokumentu/widoku, ponieważ kreatora gwarantuje poprawną architektury MFC. Jednak jeśli należy unikać, za pomocą kreatora, poniżej przedstawiono kilka metod dla architektury dokument/widok w kodzie z pominięciem:

- Traktuj dokumentu jako polecenia nieużywane i zaimplementować kod zarządzania danych w klasie widoku, zgodnie z sugestią powyżej. Obciążenie dla dokumentu jest stosunkowo niska. Pojedynczy [CDocument](../mfc/reference/cdocument-class.md) obiektu wiąże się z małej ilości obciążenie przez siebie oraz małe obciążenie związane z `CDocument`firmy klas bazowych, [CCmdTarget](../mfc/reference/ccmdtarget-class.md) i [CObject](../mfc/reference/cobject-class.md). Zarówno klasy te ostatnie są niewielkie.

   Zadeklarowane w `CDocument`:

  - Dwa `CString` obiektów.

  - Trzy **BOOL**s.

  - Jeden `CDocTemplate` wskaźnika.

  - Jeden `CPtrList` obiekt, który zawiera listę widoków dokumentu.

  Ponadto dokument wymaga ilość czasu na tworzenie obiektu dokumentu, jej obiektów widoku, okno ramek i obiektu szablonu dokumentu.

- Dokumentu i widok należy traktować jako appendages nieużywane. Umieść Twoje zarządzania danymi i kod rysowania w okno ramowe zamiast widoku. To podejście jest bliżej modelu programowania w języku C.

- Zastąp fragmenty struktura MFC, które utworzyć dokument i widok, aby wyeliminować, tworzenia ich w ogóle. Proces tworzenia dokumentu zaczyna się od wywołania `CWinApp::AddDocTemplate`. Eliminowanie wywołania od Twojej klasy aplikacji `InitInstance` elementu członkowskiego działać, a zamiast tego utworzyć okno ramowe w `InitInstance` samodzielnie. Umieść kod zarządzania danych w swojej klasie okien ramowych. Przedstawia proces tworzenia dokumentu/widoku [tworzenia dokumentu/widoku](../mfc/document-view-creation.md). Jest więcej pracy i wymaga lepiej zrozumieć Framework, ale uwalnia użytkownika wyłącznie z obciążenie dokument/widok.

Artykuł [MFC: Za pomocą klasy bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md) zapewnia bardziej konkretne przykłady alternatyw dokument/widok w kontekście aplikacji baz danych.

## <a name="see-also"></a>Zobacz także

[Architektura dokument/widok](../mfc/document-view-architecture.md)
