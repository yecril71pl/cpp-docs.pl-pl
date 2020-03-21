---
title: Tworzenie aplikacji MFC w stylu przeglądarki sieci Web
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: d928d8de34c6caab0f86e9205d0aea45b5ed737c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079449"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Tworzenie aplikacji MFC w stylu przeglądarki sieci Web

Aplikacja w stylu przeglądarki sieci Web może uzyskać dostęp do informacji z Internetu (na przykład HTML lub dokumentów aktywnych) lub intranetu, a także folderów w lokalnym systemie plików i w sieci. Dzięki wykorzystaniu klasy widoku aplikacji od [CHtmlView](../../mfc/reference/chtmlview-class.md), efektywnie można utworzyć aplikację za pomocą przeglądarki sieci Web, dostarczając widok z kontrolką WebBrowser.

### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Aby utworzyć aplikację przeglądarki sieci Web opartą na architekturze dokumentu MFC/widoku

1. Postępuj zgodnie z instrukcjami w temacie [Tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md).

1. Na stronie [Typ aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) Kreator aplikacji MFC upewnij się, że pole **Architektura dokumentu/widoku** jest zaznaczone. (Można wybrać **pojedynczy dokument** lub **wiele dokumentów**, ale nie **na podstawie okna dialogowego**).

1. Na stronie [Przejrzyj wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) Użyj menu rozwijanego **Klasa podstawowa** , aby wybrać `CHtmlView`.

1. Wybierz inne opcje, które mają być wbudowane w aplikację szkieletową.

1. Kliknij przycisk **Finish** (Zakończ).

Kontrolka WebBrowser obsługuje przeglądanie w sieci Web za pomocą hiperłączy i nawigacji Uniform Resource Locator (URL). Kontrolka utrzymuje listę historii, która umożliwia użytkownikowi przeglądanie do przodu i do tyłu przez wcześniej przeglądane witryny, foldery i dokumenty. Kontrolka bezpośrednio obsługuje nawigację, hiperłącza, listy historii, Ulubione i zabezpieczenia. Aplikacje mogą używać kontrolki WebBrowser jako kontenera dokumentów aktywnych również do hostowania dokumentów aktywnych. W związku z tym rozbudowane dokumenty, takie jak arkusze kalkulacyjne programu Microsoft Excel lub dokumenty programu Word, można otwierać i edytować w miejscu z poziomu kontrolki WebBrowser. Formant WebBrowser jest również kontenerem formantów ActiveX, który może obsługiwać dowolny formant ActiveX.

> [!NOTE]
>  Formant ActiveX WebBrowser (i w związku z tym `CHtmlView`) jest dostępny tylko dla aplikacji uruchomionych w wersjach systemu Windows, w których jest zainstalowany program Internet Explorer 4,0 lub nowszy.

Ponieważ `CHtmlView` po prostu implementuje formant przeglądarki sieci Web firmy Microsoft, jego obsługa drukowania nie jest taka sama jak w przypadku innych klas pochodnych [CView](../../mfc/reference/cview-class.md). Zamiast tego formant WebBrowser implementuje interfejs użytkownika i drukowanie drukarki. W związku z tym `CHtmlView` nie obsługuje podglądu wydruku, a struktura nie zapewnia innych funkcji obsługi drukowania: na przykład [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)i [CView:: OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), które są dostępne w innych aplikacjach MFC.

`CHtmlView` działa jako otoka dla kontrolki przeglądarka sieci Web, która umożliwia aplikacji widok w sieci Web lub stronie HTML. Kreator tworzy przesłonięcie do funkcji [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) w klasie View, dostarczając link nawigacyjny do witryny internetowej Microsoft Visual C++ :

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

Możesz zamienić tę witrynę na własną lub użyć funkcji elementu członkowskiego [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) , aby otworzyć stronę HTML, która znajduje się w skrypcie zasobów projektu jako domyślną zawartość dla tego widoku. Na przykład:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>Zobacz też

[Przykład MFCIE MFC](https://github.com/Microsoft/VCSamples)<br/>
[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Ustawianie właściwości kompilatora i Build](../../build/working-with-project-properties.md)<br/>
[Strony właściwości](../../build/reference/property-pages-visual-cpp.md)<br/>
[Ustawianie właściwości kompilatora i Build](../../build/working-with-project-properties.md)
