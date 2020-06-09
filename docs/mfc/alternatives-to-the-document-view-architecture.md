---
title: Alternatywy dla architektury widoku dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 66325d1ae087b29f59f37197fb8695504bbddbc6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619753"
---
# <a name="alternatives-to-the-documentview-architecture"></a>Alternatywy dla architektury dokument/widok

Aplikacje MFC zwykle wykorzystują architekturę dokumentu/widoku do zarządzania informacjami, formatami plików i wizualną reprezentacją danych użytkownikom. W przypadku większości aplikacji klasycznych architektura dokumentu/widoku jest odpowiednią i wydajną architekturą aplikacji. Ta architektura oddziela dane od wyświetlania i, w większości przypadków, upraszcza aplikację i zmniejsza nadmiarowy kod.

Jednak architektura dokumentu/widoku nie jest odpowiednia dla niektórych sytuacji. Rozważ następujące przykłady:

- Jeśli chcesz przenieść aplikację zapisaną w języku C dla systemu Windows, możesz chcieć zakończyć port przed dodaniem obsługi dokumentu/widoku do aplikacji.

- W przypadku pisania lekkiego narzędzia możesz się dowiedzieć, że możesz wykonać bez architektury dokument/widok.

- Jeśli oryginalny kod już miesza zarządzanie danymi przy użyciu wyświetlania danych, przeniesienie kodu do modelu dokumentu/widoku nie jest nakładu pracy, ponieważ należy je rozdzielić. Możesz chcieć pozostawić kod jako.

Aby utworzyć aplikację, która nie korzysta z architektury dokumentu/widoku, wyczyść pole wyboru **dokument/obsługa architektury** w kroku 1 Kreatora aplikacji MFC. Aby uzyskać szczegółowe informacje, zobacz [Kreator aplikacji MFC](reference/mfc-application-wizard.md) .

> [!NOTE]
> W przypadku aplikacji opartych na oknach dialogowych utworzonych przez Kreatora aplikacji MFC nie jest używana architektura dokumentu/widoku, dlatego pole wyboru **Obsługa architektury dokumentu/widoku** jest wyłączone w przypadku wybrania typu aplikacji okna dialogowego.

Kreatory Visual C++, jak również edytory źródła i okna dialogowego, pracują z wygenerowanej aplikacji tak samo jak w przypadku każdej innej aplikacji wygenerowanej przez kreatora. Aplikacja może obsługiwać paski narzędzi, ScrollBars i pasek stanu i ma pole **informacje** . Aplikacja nie będzie rejestrować żadnych szablonów dokumentów i nie będzie zawierać klasy dokumentu.

Należy zauważyć, że wygenerowana aplikacja ma klasę widoku, która `CChildView` pochodzi od `CWnd` . MFC tworzy i ustawia jedno wystąpienie klasy widoku w oknach ramowych utworzonych przez aplikację. MFC nadal wymusza korzystanie z okna widoku, ponieważ upraszcza pozycjonowanie i zarządzanie zawartością aplikacji. Możesz dodać kod do malowania do `OnPaint` elementu członkowskiego tej klasy. Kod powinien dodać paski przewijania do widoku, a nie do ramki.

Ponieważ architektura dokumentu/widoku udostępniana przez MFC jest odpowiedzialna za implementację wielu podstawowych funkcji aplikacji, jej nieobecność w projekcie oznacza, że użytkownik jest odpowiedzialny za implementację wielu ważnych funkcji aplikacji:

- Zgodnie z opisem w Kreatorze aplikacji MFC, menu aplikacji zawiera tylko **nowe** i **wyjściowe** polecenia w menu **plik** . ( **Nowe** polecenie jest obsługiwane tylko w przypadku aplikacji MDI, a nie aplikacji SDI bez obsługi dokumentu/widoku). Wygenerowany zasób menu nie będzie obsługiwał listy MRU (ostatnio używanych).

- Należy dodać funkcje i implementacje procedury obsługi dla wszystkich poleceń, które będą obsługiwane przez aplikację, w tym opcję **Otwórz** i **Zapisz** w menu **plik** . MFC zwykle udostępnia kod do obsługi tych funkcji, ale jest ściśle powiązany z architekturą dokumentu/widoku.

- Na pasku narzędzi aplikacji, jeśli zażądano takiego elementu, będzie minimalny.

Zdecydowanie zaleca się używanie Kreatora aplikacji MFC do tworzenia aplikacji bez architektury dokumentu/widoku, ponieważ Kreator gwarantuje poprawną architekturę MFC. Jeśli jednak należy unikać używania Kreatora, poniżej przedstawiono kilka metod pomijania architektury dokumentu/widoku w kodzie:

- Traktuj dokument jako nieużywany appendage i zaimplementuj kod zarządzania danymi w klasie widoku zgodnie z powyższym opisem. Obciążenie dokumentu jest stosunkowo małe. Pojedynczy obiekt [CDocument](reference/cdocument-class.md) jest niewielką ilością narzutu przez siebie i niewielkim nakładem pracy `CDocument` klas bazowych, [CCmdTarget](reference/ccmdtarget-class.md) i [CObject](reference/cobject-class.md). Obie te klasy są małe.

   Zadeklarowane w `CDocument` :

  - Dwa `CString` obiekty.

  - Trzy **bool**s.

  - Jeden `CDocTemplate` wskaźnik.

  - Jeden `CPtrList` obiekt, który zawiera listę widoków dokumentu.

  Ponadto dokument wymaga czasu na utworzenie obiektu dokumentu, jego obiektów widoku, okna ramki i obiektu szablonu dokumentu.

- Traktuj zarówno dokument, jak i widok jako nieużywane appendages. Umieść swoje zarządzanie danymi i kod rysowania w oknie ramek, a nie w widoku. To podejście jest bliżej modelu programowania języka C.

- Przesłoń części platformy MFC, które tworzą dokument i widok, aby wyeliminować ich tworzenie. Proces tworzenia dokumentu rozpoczyna się od wywołania do `CWinApp::AddDocTemplate` . Usuń to wywołanie z `InitInstance` funkcji składowej klasy aplikacji, a zamiast tego Utwórz okno ramki w `InitInstance` sobie. Umieść kod zarządzania danymi w klasie okna ramki. Proces tworzenia dokumentu/widoku jest przedstawiony w [dokumencie/Tworzenie widoku](document-view-creation.md). Jest to bardziej wydajna i wymaga dokładniejszego poznania się z platformą, ale zwalnia całkowicie z tego samego kosztu dokumentu/widoku.

Artykuł [MFC: używanie klas baz danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md) zapewnia dokładniejsze przykłady opcji dokumentu/widoku w kontekście aplikacji bazy danych.

## <a name="see-also"></a>Zobacz też

[Architektura dokumentu/widoku](document-view-architecture.md)
