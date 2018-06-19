---
title: Alternatywy dla architektury dokument widok | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 332f84346e6445fdf0550c3ddb142d9582722f0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344207"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternatywy dla architektury dokument/widok
Aplikacje MFC używać architektury dokument/widok do zarządzania informacjami, formaty plików i wizualną reprezentację danych dla użytkowników. Dla większości aplikacji klasycznych architektury dokument/widok jest Architektura aplikacji odpowiednie i skuteczne. Taka architektura oddziela danych z przeglądania i w większości przypadków, upraszcza aplikacji i zmniejsza nadmiarowy kod.  
  
 Jednak architektury dokument/widok nie jest odpowiedni dla niektórych sytuacjach. Należy wziąć pod uwagę następujące przykłady:  
  
-   Są eksportowanie aplikacji napisanych w C dla systemu Windows, możesz ukończyć portów przed dodaniem obsługi dokument/widok do aplikacji.  
  
-   Podczas pisania lekkie narzędzie może się okazać, że można wykonać bez architektury dokument/widok.  
  
-   Jeśli oryginalny kod łączy już danych zarządzania z danymi wyświetlanie, przenoszenie kod, aby model dokument/widok nie jest warto nakład pracy ponieważ muszą być rozdzielone dwa. Warto pozostawić kod jest.  
  
 Aby utworzyć aplikację, która nie korzysta z architektury dokument/widok, wyczyść **wsparcie dla architektury dokument/widok** pole wyboru w kroku 1 Kreator aplikacji MFC. Zobacz [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) szczegółowe informacje.  
  
> [!NOTE]
>  Okno dialogowe aplikacji utworzonej przez Kreatora aplikacji MFC nie używaj architektury dokument/widok, więc **wsparcie dla architektury dokument/widok** pole wyboru jest wyłączona w przypadku wybrania typu aplikacji w oknie dialogowym.  
  
 Kreatorów Visual C++, a także edytora źródła i okna dialogowe, współpracować z wygenerowanym aplikacji tak samo, jak z dowolnej generowane przez Kreatora aplikacji. Aplikacja może obsługiwać pasków narzędzi, pasków przewijania i paska stanu i ma **o** pola. Aplikacji nie będą rejestrować wszystkie szablony dokumentów i nie będzie zawierać klasę dokumentu.  
  
 Należy zauważyć, że wygenerowany aplikacji ma klasę widoku **CChildView**, pochodną `CWnd`. MFC tworzy i umieszcza jedno wystąpienie klasy widoku w ramach okna ramowe utworzone przez aplikację. MFC nadal wymusza przy użyciu okno widoku, ponieważ takie rozwiązanie upraszcza pozycjonowanie i zarządzanie zawartością aplikacji. Można dodać kod rysowania `OnPaint` członkiem tej klasy. Kod należy dodać paski przewijania, do widoku, a nie do ramki.  
  
 Ponieważ architektury dokument/widok udostępniane przez MFC jest odpowiedzialny za wdrażanie wiele podstawowych funkcji aplikacji, brak w projekcie oznacza, że użytkownik odpowiedzialnych za wdrażanie aplikacji na wiele funkcji:  
  
-   Dostarczone przez Kreatora aplikacji MFC, menu dla aplikacji zawiera tylko `New` i `Exit` polecenia w **pliku** menu. ( `New` Polecenie jest obsługiwane tylko dla aplikacji MDI, obsługuje nie SDI — aplikacje bez dokument/widok.) Menu wygenerowanego zasobów nie będzie obsługiwał listy MRU (ostatnio używane).  
  
-   Należy dodać funkcje obsługi oraz implementacji dla żadnych poleceń, które będą obsługiwać aplikacji, w tym **Otwórz** i **zapisać** na **pliku** menu. MFC zwykle zapewnia kodu do obsługi tych funkcji, ale obsługa jest ściśle powiązana z architektury dokument/widok.  
  
-   Pasek narzędzi dla aplikacji, jeśli jest to wymagane, będzie minimalny.  
  
 Zdecydowanie zaleca się użyć Kreator aplikacji MFC do tworzenia aplikacji bez architektury dokument/widok, ponieważ Kreator gwarantuje MFC o prawidłowej architekturze. Jednak jeśli należy unikać, za pomocą kreatora, poniżej przedstawiono kilka rozwiązań dla pomijanie architektury dokument/widok w kodzie:  
  
-   Traktuj dokumentu jako polecenia nieużywane i wdrożenie kodzie danych zarządzania w klasie widoku zgodnie z sugestią podaną powyżej. Obciążenie dokumentu jest stosunkowo niska. Pojedynczy [CDocument](../mfc/reference/cdocument-class.md) obiektu wiąże się z małej ilości obciążenie przez samego siebie, a także małe obciążenie związane z **CDocument**w podstawowej klasy, [CCmdTarget](../mfc/reference/ccmdtarget-class.md) i [ CObject](../mfc/reference/cobject-class.md). Oba te ostatnie klas są niewielkie.  
  
     Zadeklarowany w **CDocument**:  
  
    -   Dwa `CString` obiektów.  
  
    -   Trzy **BOOL**s.  
  
    -   Jeden `CDocTemplate` wskaźnika.  
  
    -   Jeden `CPtrList` obiekt, który zawiera listę widokach dokumentu.  
  
     Ponadto dokumentu wymaga ilość czasu, można utworzyć obiektu dokumentu, jego wyświetlanie obiektów okno ramowe i obiektu szablonu dokumentu.  
  
-   Traktuj dokumentu i widoku jako appendages nieużywane. Umieść zarządzanie danymi, a kod rysowania w oknie ramowym zamiast widoku. Ta metoda jest bliżej modelu programowania w języku C.  
  
-   Zastąpienie części programu MFC framework, które Tworzenie dokumentu i widok, aby wyeliminować na wszystkich ich tworzenia. Proces tworzenia dokumentu rozpoczyna się od wywołania `CWinApp::AddDocTemplate`. Eliminowanie tego wywołania z klasy aplikacji `InitInstance` elementu członkowskiego działać, a zamiast tego utworzyć okno ramowe w `InitInstance` samodzielnie. Umieść swój kod zarządzania danych w klasie ramki okna. Przedstawia proces tworzenia dokumentu/widoku [tworzenia dokumentu/widoku](../mfc/document-view-creation.md). To jest więcej pracy i wymaga głębsze zrozumienie struktury, ale zwalnia można wyłącznie z obciążenie dokument/widok.  
  
 Artykuł [MFC: przy użyciu klasy bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md) zawiera bardziej konkretną przykłady alternatyw dokument/widok w kontekście bazy danych aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura dokument/widok](../mfc/document-view-architecture.md)

