---
title: 'Formanty MFC ActiveX: Licencjonowanie formantu ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COleObjectFactory
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 725e6cf167ec01635a3072f09ecaa2f5055b1891
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353938"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX
Licencjonowania pomocy technicznej, opcjonalna funkcja formantów ActiveX służy do kontrolowania, kto może używać lub rozkładanie formantu. (Aby uzyskać dodatkowe informacje dotyczące licencjonowania, zobacz licencjonowania problemy w [Uaktualnianie istniejącego formantu ActiveX](../mfc/upgrading-an-existing-activex-control.md).)  
  
 W tym artykule omówiono następujące zagadnienia:  
  
-   [Omówienie formantu ActiveX licencjonowania](#_core_overview_of_activex_control_licensing)  
  
-   [Tworzenie formantu licencjonowane](#_core_creating_a_licensed_control)  
  
-   [Obsługa licencjonowania](#_core_licensing_support)  
  
-   [Dostosowywanie Licencjonowanie formantu ActiveX](#_core_customizing_the_licensing_of_an_activex_control)  
  
 Formanty ActiveX, które implementują licencjonowania pozwalają Deweloper kontroli, aby określić, jak inne osoby użyje formantu ActiveX. Podaj nabywca formantu za pomocą formantu i. Plik — Umowa licencyjna, za zgodą czy nabywca może dystrybuować formantu, ale nie. Plik — Umowa licencyjna z aplikacji, która używa kontrolki. Zapobiega to użytkowników tej aplikacji z zapisywania nowych aplikacji, które używają formantu, bez pierwszy Licencjonowanie kontrolki użytkownika.  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> Omówienie formantu ActiveX licencjonowania  
 Aby zapewnić obsługę licencjonowania dla formantów ActiveX [coleobjectfactory —](../mfc/reference/coleobjectfactory-class.md) klasa zawiera implementację kilka funkcji w **IClassFactory2** interfejsu: **IClassFactory2 :: RequestLicKey**, **IClassFactory2::GetLicInfo**, i **IClassFactory2::CreateInstanceLic**. Gdy deweloper aplikacji kontenera wysyła żądanie można utworzyć wystąpienia formantu wywołania `GetLicInfo` nawiązać upewnij się, że formant. Plik — Umowa licencyjna jest obecny. Jeśli formant ma licencję, można tworzyć i umieszczane w kontenerze wystąpienia formantu. Po zakończeniu dewelopera konstruowanie aplikacji kontenera innej funkcji, ten czas połączenia do `RequestLicKey`, staje się. Ta funkcja zwraca klucz licencji (ciąg znaków proste) do aplikacji kontenera. Zwrócony klucza zostaje następnie osadzony w aplikacji.  
  
 Na poniższej ilustracji przedstawiono Weryfikacja licencji formantu ActiveX, który będzie używany podczas tworzenia aplikacji kontenera. Jak wspomniano wcześniej, Deweloper aplikacji kontenera musi być poprawne. Plik — Umowa licencyjna zainstalowane na komputerze deweloperskim, można utworzyć wystąpienia formantu.  
  
 ![Licencjonowane zweryfikowało Programowanie formantów ActiveX](../mfc/media/vc374d1.gif "vc374d1")  
Podczas tworzenia weryfikacji licencjonowanego formantu ActiveX  
  
 Następny proces przedstawiono na poniższej ilustracji, występuje, gdy użytkownik końcowy uruchamia aplikację kontenera.  
  
 Po uruchomieniu aplikacji wystąpienia formantu zwykle musi zostać utworzona. Kontener rozwiązanie to wywołania do `CreateInstanceLic`, przekazując klucz licencji osadzony jako parametr. Porównanie ciągów jest przeprowadzane między kluczem licencji osadzonych i własne kontrolki kopię klucza licencji. Gdy dopasowanie jest pomyślne, tworzone jest wystąpienie formantu i aplikacja kontynuuje wykonywanie normalnie. Należy pamiętać, że. Plik — Umowa licencyjna nie musi być obecny na komputerze użytkownika formant.  
  
 ![Licencjonowane formantu ActiveX zweryfikowało wykonywania](../mfc/media/vc374d2.gif "vc374d2")  
Weryfikacja licencjonowanego formantu ActiveX podczas wykonywania  
  
 Licencjonowanie formantu zawiera dwa składniki podstawowe: określony kod w implementacji sterowania biblioteki DLL i plików licencji. Kod składa się z dwóch (lub prawdopodobnie trzy) wywołania funkcji i ciąg znaków, zwanych "ciąg licencji", zawierający informacje o prawach autorskich. Te wywołania i parametry licencji znajdują się w implementacji formantu (. Pliku CPP). Plik licencji, generowane przez kreatora formantu ActiveX, jest plikiem tekstowym o informację o prawach autorskich. Nosi przy użyciu nazwy projektu z. Rozszerzenie — Umowa licencyjna, na przykład próbki. — UMOWA LICENCYJNA. Licencjonowanego formantu należy dołączyć plik licencji w razie potrzeby jest używany w czasie projektowania.  
  
##  <a name="_core_creating_a_licensed_control"></a> Tworzenie formantu licencjonowane  
 Kreator kontrolek ActiveX umożliwia tworzenie framework kontroli, jest łatwy do uwzględnienia licencjonowania pomocy technicznej. Po określeniu, że formant powinien mieć licencji, Kreator kontrolek ActiveX dodaje kod do klasy formantu do obsługi licencjonowania. Kod składa się z funkcji, które przy użyciu pliku klucza i licencji na potrzeby weryfikacji licencji. Te funkcje także można zmodyfikować, aby dostosować Licencjonowanie formantu. Aby uzyskać więcej informacji dotyczących dostosowywania licencji, zobacz [Dostosowywanie Licencjonowanie formantu ActiveX](#_core_customizing_the_licensing_of_an_activex_control) dalszej części tego artykułu.  
  
#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Aby dodać obsługę licencjonowania przy użyciu Kreatora formantu ActiveX, podczas tworzenia projektu kontroli  
  
1.  Postępuj zgodnie z instrukcjami w [tworzenia kontrolki ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). **Ustawienia aplikacji** strony Kreator kontrolek ActiveX zawiera opcję utworzenia formantu z licencji.  
  
 Kreator kontrolek ActiveX generuje strukturę formantu ActiveX, która podstawowa obsługuje licencjonowania. Aby uzyskać szczegółowy opis licencjonowania kod zobacz temat dalej.  
  
##  <a name="_core_licensing_support"></a> Obsługa licencjonowania  
 Gdy Kreator kontrolek ActiveX umożliwia dodawanie obsługi licencjonowania do formantu ActiveX, Kreator kontrolek ActiveX dodaje kod, który deklaruje i implementuje licencjonowania możliwości zostanie dodany do formantu nagłówka i implementacji plików. Ten kod składa się z `VerifyUserLicense` funkcji członkowskiej i `GetLicenseKey` funkcji Członkowskich zastąpienia domyślnej implementacji w [coleobjectfactory —](../mfc/reference/coleobjectfactory-class.md) . Te funkcje pobrać i zweryfikować licencji formantu.  
  
> [!NOTE]
>  Trzeci funkcji członkowskiej `VerifyLicenseKey` nie jest generowany przez Kreator kontrolek ActiveX, ale może zostać zastąpiona w celu dostosować zachowanie weryfikacji klucza licencji.  
  
 Funkcje Członkowskie są:  
  
-   [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)  
  
     Sprawdza, czy formant umożliwia wykorzystanie czasu projektowania przez system na obecność pliku licencji sterowania sprawdzania. Ta funkcja jest wywoływana przez platformę w ramach przetwarzania **IClassFactory2::GetLicInfo** i **IClassFactory::CreateInstanceLic**.  
  
-   [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)  
  
     Żąda Unikatowy klucz z formantu biblioteki DLL. Ten klucz jest osadzony w aplikacji kontenera i później, używany w połączeniu z `VerifyLicenseKey`, można utworzyć wystąpienia formantu. Ta funkcja jest wywoływana przez platformę w ramach przetwarzania **IClassFactory2::RequestLicKey**.  
  
-   [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)  
  
     Sprawdza, czy klucz osadzonych i formantu Unikatowy klucz są takie same. Dzięki temu kontener można utworzyć wystąpienia formantu jej wykorzystanie. Ta funkcja jest wywoływana przez platformę w ramach przetwarzania **IClassFactory2::CreateInstanceLic** i może zostać zastąpiona zapewnienie dostosowane weryfikacji klucza licencji. Domyślna implementacja wykonuje porównania ciągów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Licencjonowanie formantu ActiveX](#_core_customizing_the_licensing_of_an_activex_control)w dalszej części tego artykułu.  
  
###  <a name="_core_header_file_modifications"></a> Modyfikacja pliku nagłówka  
 Kreator kontrolek ActiveX umieszcza następujący kod w pliku nagłówka. W tym przykładzie dwóch funkcji Członkowskich `CSampleCtrl`przez obiekt `factory` został zadeklarowany, jedną, która sprawdza obecność formantu. Plik — Umowa licencyjna i innego, która pobiera klucz licencji do użycia w aplikacji zawierająca formant:  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> Modyfikacje plików implementacji  
 Kreator kontrolek ActiveX umieszcza następujące dwie instrukcje w pliku implementacji Aby zadeklarować ciągu filename licencji i licencji:  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  Jeśli zmodyfikujesz **szLicString** w dowolny sposób, musisz także zmodyfikować pierwszego wiersza w formancie. Plik — Umowa licencyjna lub licencjonowania nie będzie działać prawidłowo.  
  
 Kreator kontrolek ActiveX umieszcza następujący kod w pliku implementacji sterowania, aby określić klasy formantu `VerifyUserLicense` i `GetLicenseKey` funkcje:  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 Na koniec **Kreator kontrolek ActiveX** modyfikuje projektu kontroli. Plik IDL. **Licencjonowane** — słowo kluczowe jest dodawany do deklaracji klasy coclass kontroli, jak w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Dostosowywanie Licencjonowanie formantu ActiveX  
 Ponieważ `VerifyUserLicense`, `GetLicenseKey`, i `VerifyLicenseKey` są deklarowane jako funkcje wirtualny element członkowski klasy fabryki sterowania, można dostosować zachowanie licencjonowania formantu.  
  
 Na przykład można podać kilka poziomów licencjonowania dla formantu przez zastąpienie `VerifyUserLicense` lub `VerifyLicenseKey` funkcji elementów członkowskich. Wewnątrz tej funkcji można dostosować, których właściwości lub metody są widoczne dla użytkownika, zgodnie z poziomu licencji zostało wykryte.  
  
 Można również dodać kod `VerifyLicenseKey` funkcja, która udostępnia metodę dostosowane dla informujące użytkownika, który kontroluje tworzenie nie powiodło się. Na przykład w sieci `VerifyLicenseKey` polu funkcji członkowskiej, użytkownik może zostać wyświetlony komunikat informujący formantu nie można zainicjować i dlaczego.  
  
> [!NOTE]
>  Innym sposobem dostosowania Weryfikacja licencji formantu ActiveX jest sprawdzenie bazy danych rejestracji dla określonego klucza rejestru, zamiast wywoływać metodę `AfxVerifyLicFile`. Na przykład domyślna implementacja zobacz [modyfikacje plików implementacji](#_core_implementation_file_modifications) sekcji tego artykułu.  
  
 Aby uzyskać dodatkowe informacje dotyczące licencjonowania, zobacz licencjonowania problemy w [Uaktualnianie istniejącego formantu ActiveX](../mfc/upgrading-an-existing-activex-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)

