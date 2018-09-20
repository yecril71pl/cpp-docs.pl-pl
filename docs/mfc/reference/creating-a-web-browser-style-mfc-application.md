---
title: Tworzenie aplikacji MFC w stylu przeglądarki sieci Web | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcweb.project
dev_langs:
- C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae8f516da368631e727cf302f85ab33ea31f608
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397679"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Tworzenie aplikacji MFC w stylu przeglądarki sieci Web

Aplikacji w stylu przeglądarki sieci Web można uzyskać dostęp do informacji w Internecie (takich jak HTML lub dokumenty aktywne) lub intranet, a także folderów w lokalnym systemie plików, a w sieci. Przez wyprowadzanie klasy widoku aplikacji z [CHtmlView](../../mfc/reference/chtmlview-class.md), efektywnie uczynić przeglądarki sieci Web aplikacji przesyłając widoku za pomocą formantu WebBrowser.

### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Aby utworzyć aplikację przeglądarki sieci Web, w zależności od architektury dokument/widok MFC

1. Postępuj zgodnie z instrukcjami [tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md).

1. W Kreatorze aplikacji MFC [typ aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) strony, należy pewne, że **architektury dokument/widok** pole jest zaznaczone. (Możesz wybrać dowolną **pojedynczego dokumentu** lub **wiele dokumentów**, ale nie **oparte o okna dialogowe**.)

1. Na [przeglądu wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) stronie **klasy bazowej** menu rozwijanego, aby wybrać `CHtmlView`.

1. Wybierz odpowiednie opcje mają wbudowaną szkielet aplikacji.

1. Kliknij przycisk **Zakończ**.

WebBrowser — formant obsługuje przeglądanie sieci Web za pomocą hiperlinków i nawigacja Uniform Resource Locator (URL). Formant utrzymuje listę historii, który umożliwia użytkownikowi przejść do przodu i wstecz za pośrednictwem wcześniej przeglądane witryn, folderów i dokumentów. Kontrolka bezpośrednio obsługuje nawigacji, hiperłącza, listy historii, ulubionych i zabezpieczeń. Aplikacje mogą używać kontrolki WebBrowser jako kontener aktywnego dokumentu na hoście również dokumenty aktywne. W związku z tym Bogato sformatowane dokumenty, takie jak arkusze kalkulacyjne programu Excel lub dokumentów programu Word umożliwia otwarty i edytowany w miejscu z wewnątrz formantu WebBrowser. WebBrowser — formant jest również kontener formantu ActiveX, który może obsługiwać dowolną kontrolkę ActiveX.

> [!NOTE]
>  Kontrolki WebBrowser ActiveX (i w związku z tym `CHtmlView`) jest dostępna tylko dla aplikacji działających w ramach wersji Windows, w której program Internet Explorer 4.0 lub nowszy został zainstalowany.

Ponieważ `CHtmlView` po prostu implementuje dodatek Microsoft Web formantu przeglądarki, jego obsługa drukowania jest podobnie jak inne [CView](../../mfc/reference/cview-class.md)-klas pochodnych. Zamiast formantu WebBrowser implementuje interfejs użytkownika drukarki i drukowania. W rezultacie `CHtmlView` jest podgląd wydruku nie jest obsługiwane i nie zapewnia platformę dla innych funkcji drukowania pomocy technicznej: na przykład [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), i [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), które są dostępne w innych aplikacjach MFC.

`CHtmlView` działa jako otoki dla formantu przeglądarki sieci Web, co daje aplikacji widoku sieci Web lub strony HTML na. Kreator utworzy zastąpienie [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) funkcja w klasie widoku, zapewniając łącze nawigacyjne do witryny sieci Web firmy Microsoft Visual C++:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
        NULL,
        NULL);
}
```

Możesz zastąpić tę lokację własny, możesz też [loadfromresource —](../../mfc/reference/chtmlview-class.md#loadfromresource) funkcja elementu członkowskiego, aby otworzyć stronę HTML, która znajduje się w skrypt zasobów projektu jako domyślnej zawartości widoku. Na przykład:

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

[Próbki MFC MFCIE](https://github.com/Microsoft/VCSamples)<br/>
[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Praca z właściwościami projektu](../../ide/working-with-project-properties.md)<br/>
[Strony właściwości](../../ide/property-pages-visual-cpp.md)<br/>
[Praca z właściwościami projektu](../../ide/working-with-project-properties.md)


