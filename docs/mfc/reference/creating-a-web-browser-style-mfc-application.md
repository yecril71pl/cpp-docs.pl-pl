---
title: "Tworzenie aplikacji MFC w stylu przeglądarki sieci Web | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfcweb.project
dev_langs: C++
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c88ca61fb7dfdfbe90ed3b460c0fe9bc3a045ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Tworzenie aplikacji MFC w stylu przeglądarki sieci Web
Do aplikacji w stylu przeglądarki sieci Web ma dostęp do informacji z Internetu (na przykład HTML lub aktywne dokumenty) lub intranet, jak również folderów w lokalnym systemie plików, a w sieci. Przez wyprowadzanie klasy widoku aplikacji z [CHtmlView](../../mfc/reference/chtmlview-class.md), efektywnie ułatwić przeglądarki sieci Web aplikacji, zapewniając widoku za pomocą formantu WebBrowser.  
  
### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Aby utworzyć aplikację przeglądarki sieci Web oparta na architekturze dokument/widok MFC  
  
1.  Postępuj zgodnie z instrukcjami w [tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  W Kreatorze aplikacji MFC [typu aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) upewnij niektórych, że **architektury dokument/widok** zaznaczone pole. (Można wybrać **pojedynczego dokumentu** lub **wielu dokumentów**, ale nie **okno dialogowe na podstawie**.)  
  
3.  Na [Przejrzyj wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) użyj **klasa podstawowa** menu rozwijanego, aby wybrać `CHtmlView`.  
  
4.  Wybierz odpowiednie opcje mają wbudowane szkielet aplikacji.  
  
5.  Kliknij przycisk **Zakończ**.  
  
 Formant WebBrowser obsługuje przeglądanie sieci Web za pomocą hiperłączy i nawigacja Uniform Resource Locator (URL). Formant obsługuje listy historii, który umożliwia użytkownikowi przeglądanie do przodu i do tyłu za pośrednictwem wcześniej przeglądanie witryn, folderów i dokumentów. Formant obsługuje bezpośrednio nawigacji, hiperłącza, listy historii, ulubionymi i zabezpieczeń. Aplikacje mogą używać formantu WebBrowser jako kontener dokumentów aktywnych do hosta także dokumenty aktywne. W związku z tym Bogato sformatowane dokumentów, takich jak arkusze kalkulacyjne programu Microsoft Excel lub dokumentów programu Word może zostać otwarty i edytowany w miejscu z wewnątrz formantu WebBrowser. Formant WebBrowser jest również kontenera formantu ActiveX, który może obsługiwać formantu ActiveX.  
  
> [!NOTE]
>  Formant WebBrowser ActiveX (i w związku z tym `CHtmlView`) jest dostępna tylko dla aplikacji uruchomionych w wersjach systemu Windows, w których Internet Explorer w wersji 4.0 lub nowszy został zainstalowany.  
  
 Ponieważ `CHtmlView` po prostu implementuje formant przeglądarki Microsoft Web, jego obsługę drukowania nie jest jak inny [CView](../../mfc/reference/cview-class.md)-klas pochodnych. Zamiast formant WebBrowser implementuje interfejs użytkownika drukarki i wydruku. W związku z tym `CHtmlView` jest obsługuje Podgląd wydruku i nie zapewnia platformę dla innych funkcji obsługi drukowania: na przykład [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), i [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), które są dostępne w innych aplikacjach MFC.  
  
 `CHtmlView`działa jako otoka dla formant przeglądarki sieci Web, co daje aplikacji widoku na sieci Web lub strony HTML. Kreator tworzy zastąpienia [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) funkcji w klasie widoku udostępnienie łącza nawigacji do witryny sieci Web Microsoft Visual C++:  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
    NULL,
    NULL);

} 
```  
  
 Tej witryny można zastąpić własny lub użyć [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) funkcji członkowskiej, aby otworzyć stronę HTML, która znajduje się w skrypt zasobów projektu jako domyślnej zawartości widoku. Na przykład:  
  
```  
void CWebView::OnInitialUpdate()  
{  
    CHtmlView::OnInitialUpdate();

 *// TODO: This code navigates to a popular spot on the web. *//  change the code to go where you'd like.  
    LoadFromResource(IDR_HTML1);

} 
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MFCIE](http://msdn.microsoft.com/en-us/7391aa0c-fca8-4994-a6c9-6c5c7470fba0)   
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Praca z właściwościami projektu](../../ide/working-with-project-properties.md)   
 [Strony właściwości](../../ide/property-pages-visual-cpp.md)   
 [Praca z właściwościami projektu](../../ide/working-with-project-properties.md)   
 [Wdrażanie aplikacji](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)

