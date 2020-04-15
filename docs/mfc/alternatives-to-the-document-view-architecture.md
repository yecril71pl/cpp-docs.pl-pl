---
title: Alternatywy dla architektury widoku dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 41af30d25d7ddb9e2bdbb7a0f7b86cb741ae1048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370798"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternatywy dla architektury dokument/widok

Aplikacje MFC zwykle używają architektury dokumentu/widoku do zarządzania informacjami, formatami plików i wizualną reprezentacją danych dla użytkowników. W przypadku większości aplikacji klasycznych architektura dokumentu/widoku jest odpowiednią i wydajną architekturą aplikacji. Ta architektura oddziela dane od wyświetlania i, w większości przypadków, upraszcza aplikację i zmniejsza nadmiarowy kod.

Jednak architektura dokumentu/widoku nie jest odpowiednia dla niektórych sytuacji. Rozważmy następujące przykłady:

- Jeśli przenosisz aplikację napisaną w języku C dla systemu Windows, możesz chcieć ukończyć port przed dodaniem obsługi dokumentu/widoku do aplikacji.

- Jeśli piszesz lekkie narzędzie, może się okazać, że można zrobić bez architektury dokumentu/widoku.

- Jeśli oryginalny kod już miesza zarządzanie danymi z wyświetlaniem danych, przeniesienie kodu do modelu dokumentu/widoku nie jest warte wysiłku, ponieważ należy je oddzielić. Może wolisz zostawić kod w stanie, w jakim jest.

Aby utworzyć aplikację, która nie używa architektury dokumentu/widoku, wyczyść pole wyboru **Obsługa architektury dokumentu/widoku** w kroku 1 Kreatora aplikacji MFC. Szczegółowe informacje można znaleźć [w Kreatorze aplikacji MFC.](../mfc/reference/mfc-application-wizard.md)

> [!NOTE]
> Aplikacje oparte na oknach dialogowych tworzone przez Kreatora aplikacji MFC nie używają architektury dokumentu/widoku, więc pole wyboru **Obsługa architektury dokumentu/widoku** jest wyłączone po wybraniu typu aplikacji okna dialogowego.

Kreatorzy języka Visual C++, a także edytory źródeł i okien dialogowych, działają z wygenerowaną aplikacją tak samo, jak z dowolną inną aplikacją generowaną przez kreatora. Aplikacja może obsługiwać paski narzędzi, paski przewijania i pasek stanu i ma pole **Informacje.** Aplikacja nie zarejestruje żadnych szablonów dokumentów i nie będzie zawierać klasy dokumentu.

Należy zauważyć, że wygenerowana `CChildView`aplikacja ma `CWnd`klasę widoku, pochodzi od . MFC tworzy i pozycjonuje jedno wystąpienie klasy widoku w oknach ramki utworzonych przez aplikację. MFC nadal wymusza przy użyciu okna widoku, ponieważ upraszcza pozycjonowanie i zarządzanie zawartością aplikacji. Można dodać kod malowania do `OnPaint` członka tej klasy. Kod należy dodać paski przewijania do widoku, a nie do ramki.

Ponieważ architektura dokumentu/widoku dostarczona przez MFC jest odpowiedzialna za implementowanie wielu podstawowych funkcji aplikacji, jej brak w projekcie oznacza, że jesteś odpowiedzialny za implementowanie wielu ważnych funkcji aplikacji:

- Zgodnie z instrukcjami Kreatora aplikacji MFC menu aplikacji zawiera tylko polecenia **Nowe** i **Zakończ** w menu **Plik.** (Polecenie **Nowy** jest obsługiwane tylko dla aplikacji MDI, a nie aplikacji SDI bez obsługi dokumentu/widoku). Wygenerowany zasób menu nie będzie obsługiwał listy MRU (ostatnio używanej).

- Należy dodać funkcje obsługi i implementacje dla wszystkich poleceń, które aplikacja będzie obsługiwać, w tym **Otwórz** i **Zapisz** w menu **Plik.** MFC zwykle zapewnia kod do obsługi tych funkcji, ale ta obsługa jest ściśle powiązana z architekturą dokumentu/widoku.

- Pasek narzędzi dla aplikacji, jeśli zażądano jednego, będzie minimalny.

Zdecydowanie zaleca się, aby używać Kreatora aplikacji MFC do tworzenia aplikacji bez architektury dokumentu/widoku, ponieważ kreator gwarantuje poprawną architekturę MFC. Jeśli jednak należy unikać korzystania z kreatora, oto kilka metod pomijania architektury dokumentu/widoku w kodzie:

- Traktuj dokument jako nieużywane dodatek i zaimplementuj kod zarządzania danymi w klasie widoku, zgodnie z powyższą sugestią. Obciążenie dla dokumentu jest stosunkowo niskie. Pojedynczy obiekt [CDocument](../mfc/reference/cdocument-class.md) ponosi niewielką ilość narzutów przez siebie, `CDocument`plus małe obciążenie 's klas podstawowych, [CCmdTarget](../mfc/reference/ccmdtarget-class.md) i [CObject](../mfc/reference/cobject-class.md). Obie te ostatnie klasy są małe.

   Zadeklarowane `CDocument`w:

  - Dwa `CString` obiekty.

  - Trzy **BOOL**s.

  - Jeden `CDocTemplate` wskaźnik.

  - Jeden `CPtrList` obiekt, który zawiera listę widoków dokumentu.

  Ponadto dokument wymaga czasu na utworzenie obiektu dokumentu, jego obiektów widoku, okna ramki i obiektu szablonu dokumentu.

- Traktuj zarówno dokument, jak i widok jako nieużywane przydatki. Umieść kod zarządzania danymi i rysunku w oknie ramki, a nie w widoku. Takie podejście jest bliżej modelu programowania języka C.

- Zastąpokaj części struktury MFC, które tworzą dokument i widok, aby wyeliminować ich tworzenie w ogóle. Proces tworzenia dokumentu rozpoczyna się `CWinApp::AddDocTemplate`od wywołania . Wyeliminuj to `InitInstance` wywołanie z funkcji elementu członkowskiego klasy `InitInstance` aplikacji i zamiast tego utwórz okno ramki w sobie. Umieść kod zarządzania danymi w klasie okna ramki. Proces tworzenia dokumentu/widoku jest zilustrowany w [dokumencie/utworzeniu widoku](../mfc/document-view-creation.md). Jest to więcej pracy i wymaga głębszego zrozumienia struktury, ale zwalnia całkowicie z dokumentu/widoku narzutów.

Artykuł [MFC: Korzystanie z klas bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md) zawiera bardziej konkretne przykłady alternatyw dokumentu/widoku w kontekście aplikacji bazy danych.

## <a name="see-also"></a>Zobacz też

[Architektura dokumentu/widoku](../mfc/document-view-architecture.md)
