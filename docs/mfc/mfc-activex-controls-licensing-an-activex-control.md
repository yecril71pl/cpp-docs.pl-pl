---
title: 'Kontrolki ActiveX MFC: Licencjonowanie kontrolki ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 451cf4b404143ce8f9b94481dd27227f487874d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381169"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX

Licencjonowanie pomocy technicznej, opcjonalna funkcja formantów ActiveX pozwala na kontrolowanie, kto ma możliwość używania i rozpowszechniania formantu. (Dodatkowe Omówienie licencjonowania problemów, można znaleźć w temacie licencjonowania problemy w [Uaktualnianie istniejącego kontrolki ActiveX](../mfc/upgrading-an-existing-activex-control.md).)

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).

W tym artykule omówiono następujące tematy:

- [Omówienie formantu ActiveX licencjonowania](#_core_overview_of_activex_control_licensing)

- [Tworzenie licencjonowany formant](#_core_creating_a_licensed_control)

- [Obsługa licencjonowania](#_core_licensing_support)

- [Dostosowywanie Licencjonowanie kontrolki ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Kontrolki ActiveX, które implementują licencjonowania pozwalają Deweloper kontrolki do określenia, jak używać kontrolki ActiveX przez inne osoby. Podaj nabywca sterowania za pomocą kontrolki i. Plik — Umowa licencyjna, z umową, że odbiorcy mogą przekazywać kontrolki, ale nie. Plik — Umowa licencyjna, za pomocą aplikacji, która używa kontrolki. Uniemożliwia to użytkownikom tę aplikację z pisania nowych aplikacji, które używają formantu, bez pierwszy licencjonowania kontroli ze strony użytkownika.

##  <a name="_core_overview_of_activex_control_licensing"></a> Omówienie formantu ActiveX licencjonowania

Aby zapewnić obsługę licencjonowania formantów ActiveX [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) klasa zawiera implementację kilka funkcji w `IClassFactory2` interfejsu: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`, i `IClassFactory2::CreateInstanceLic`. Gdy deweloper aplikacji kontenera sprawia, że żądanie, aby utworzyć wystąpienie kontrolki, wywołanie `GetLicInfo` nawiązać upewnij się, że formant. Plik — Umowa licencyjna jest obecny. Jeśli kontrolka ma licencję, można tworzyć wystąpienia formantu i znajduje się w kontenerze. Po zakończeniu dewelopera podczas tworzenia aplikacji kontenera, wywołać inną funkcję, w tym momencie `RequestLicKey`, jest wykonywane. Ta funkcja zwraca klucz licencji (ciąg znaków prosty) do aplikacji kontenera. Zwrócony klucz jest następnie osadzany w aplikacji.

Na poniższym rysunku przedstawiono weryfikacji licencji formantu ActiveX, który będzie używany podczas tworzenia aplikacji kontenera. Jak wspomniano wcześniej, Deweloper aplikacji kontenera musi być prawidłowe. Plik — Umowa licencyjna zainstalowane na komputerze deweloperskim, aby utworzyć wystąpienie kontrolki.

![Licencjonowany formant ActiveX zweryfikowanych w rozwoju](../mfc/media/vc374d1.gif "vc374d1") weryfikacji licencjonowane ActiveX sterowania podczas programowania

Następny proces, pokazano na poniższym rysunku, występuje, gdy użytkownik końcowy uruchamia aplikację kontenera.

Po uruchomieniu aplikacji wystąpienie kontrolki zwykle musi zostać utworzona. Kontener rozwiązanie to wywołuje element `CreateInstanceLic`, przekazując klucz licencji osadzony jako parametr. Porównanie ciągów jest podejmowana między kluczem licencji osadzone i własne kontrolki kopię klucza licencji. Jeśli dopasowanie się powiedzie, tworzone jest wystąpienie kontrolki, a aplikacja kontynuuje wykonywanie normalnie. Należy pamiętać, że. Plik — Umowa licencyjna nie muszą być obecne na komputerze użytkownika kontroli.

![Licencjonowany formant ActiveX zweryfikowany w ramach wykonywania](../mfc/media/vc374d2.gif "vc374d2") weryfikacji licencji ActiveX kontrolowanie podczas wykonywania

Licencjonowania formantów składa się z dwóch podstawowych składników: określony kod w celu wykonania formantu biblioteki DLL i pliku licencji. Kod składa się z dwóch (lub prawdopodobnie trzy) wywołania funkcji i ciąg znaków, zwanych "licencji ciąg", zawierający informacje o prawach autorskich. Te wywołania i ciąg licencji znajdują się w implementacji kontroli (. Plik CPP). Plik licencji, generowane przez kreatora kontrolek ActiveX, jest plikiem tekstowym o prawach autorskich. Jest on nazwany przy użyciu nazwy projektu za pomocą. Rozszerzenie — Umowa licencyjna, na przykład próbki. — UMOWA LICENCYJNA. Licencjonowany formant musi towarzyszyć przy użyciu pliku licencji, jeśli są potrzebne podczas projektowania.

##  <a name="_core_creating_a_licensed_control"></a> Tworzenie licencjonowany formant

Jeśli użyjesz kreatora kontrolek ActiveX do utworzenia w ramach kontroli jest łatwe obejmują wsparcie licencjonowania. Po określeniu, czy kontrolka powinny mieć licencji czasu wykonywania, Kreator kontrolek ActiveX dodaje kod do klasy formantu do obsługi licencjonowania. Kod składa się z funkcji, które przy użyciu pliku klucza i licencji dla weryfikacji licencji. Te funkcje także można zmodyfikować, aby dostosować licencjonowania formantów. Aby uzyskać więcej informacji na temat dostosowywania licencji, zobacz [Dostosowywanie Licencjonowanie kontrolki ActiveX](#_core_customizing_the_licensing_of_an_activex_control) w dalszej części tego artykułu.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Aby dodać obsługę licencjonowania za pomocą Kreatora kontrolek ActiveX, podczas tworzenia projektu kontroli

1. Postępuj zgodnie z instrukcjami w [tworzenia kontrolki ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). **Ustawienia aplikacji** strony kreatora kontrolek ActiveX zawiera opcję tworzenia kontrolki za pomocą licencji czasu wykonywania.

Kreator kontrolek ActiveX generuje platforma formantu ActiveX, która obejmuje podstawowej pomocy technicznej licencjonowania. Aby uzyskać szczegółowy opis licencjonowania kodu zobacz następny temat.

##  <a name="_core_licensing_support"></a> Obsługa licencjonowania

Korzystając z Kreatora kontrolek ActiveX dodać obsługę licencjonowania do formantu ActiveX, Kreator kontrolek ActiveX dodaje kod, który deklaruje i implementuje funkcję licencjonowania jest dodawany do formantu nagłówka i implementacji plików. Ten kod składa się z `VerifyUserLicense` funkcja elementu członkowskiego i `GetLicenseKey` składowa zastąpienia domyślnej implementacji w [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Tych funkcji, Pobierz i Zweryfikuj licencji formantu.

> [!NOTE]
>  Trzecia funkcja członkowska `VerifyLicenseKey` nie są generowane przez kreatora kontrolek ActiveX, ale może zostać zastąpiona w celu dostosowywania zachowania klucza weryfikacji licencji.

Te funkcje elementów członkowskich są następujące:

- [Verifyuserlicense —](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

     Sprawdza, czy kontrolka zezwala na użycie w czasie projektowania, sprawdzając systemu pod kątem obecności pliku licencji formantu. Ta funkcja jest wywoływana przez framework jako część przetwarzania `IClassFactory2::GetLicInfo` i `IClassFactory::CreateInstanceLic`.

- [Getlicensekey —](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

     Żąda Unikatowy klucz z formantu biblioteki DLL. Ten klucz jest osadzony w aplikacji kontenera i później używany w połączeniu z `VerifyLicenseKey`, aby utworzyć wystąpienie kontrolki. Ta funkcja jest wywoływana przez framework jako część przetwarzania `IClassFactory2::RequestLicKey`.

- [Verifylicensekey —](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

     Sprawdza, czy osadzony klucz i unikatowy klucz formantu są takie same. Umożliwia to kontener, aby utworzyć wystąpienie kontrolki w ramach jego użycia. Ta funkcja jest wywoływana przez framework jako część przetwarzania `IClassFactory2::CreateInstanceLic` i może zostać zastąpiona w celu zapewniają dostosowane weryfikację klucza licencji. Domyślna implementacja wykonuje porównanie ciągu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Licencjonowanie kontrolki ActiveX](#_core_customizing_the_licensing_of_an_activex_control), w dalszej części tego artykułu.

###  <a name="_core_header_file_modifications"></a> Modyfikacje plików nagłówka

Kreator kontrolek ActiveX umieszcza następujący kod w pliku nagłówka. W tym przykładzie dwie funkcje elementów członkowskich `CSampleCtrl`przez obiekt `factory` są deklarowane, taki, który sprawdza obecność formantu. Plik — Umowa licencyjna i drugiego, która pobiera klucz licencji, który będzie używany w aplikacji zawierający kontrolki:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a> Implementacja modyfikacje plików

Kreator kontrolek ActiveX umieszcza następujące dwie instrukcje w pliku implementacji do deklarowania licencji, nazwa_pliku i ciąg licencji:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  Jeśli zmodyfikujesz `szLicString` w jakikolwiek sposób, musisz także zmodyfikować pierwszy wiersz w kontrolce. Plik — Umowa licencyjna lub licencjonowania nie będzie działać prawidłowo.

Kreator kontrolek ActiveX umieszcza następujący kod w pliku implementacji do definiowania klasy kontrolek `VerifyUserLicense` i `GetLicenseKey` funkcje:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Na koniec **kreatora kontrolek ActiveX** modyfikuje projekt kontroli. Plik IDL. **Licencjonowane** — słowo kluczowe jest dodawany do deklaracji klasy coclass kontroli, jak w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Dostosowywanie Licencjonowanie kontrolki ActiveX

Ponieważ `VerifyUserLicense`, `GetLicenseKey`, i `VerifyLicenseKey` są deklarowane jako funkcji wirtualnych elementów członkowskich klasy fabryki kontrolki, można dostosować zachowanie licencjonowania formantu.

Na przykład można dostarczyć kilka poziomów licencjonowania dla formantu przez zastąpienie `VerifyUserLicense` lub `VerifyLicenseKey` funkcji elementów członkowskich. Wewnątrz tej funkcji można dostosować, które właściwości lub metody, które są widoczne dla użytkownika, zgodnie z poziomem licencji, które zostało wykryte.

Można również dodać kod, aby `VerifyLicenseKey` funkcja, która udostępnia metody dostosowane dla informujące użytkownika, które sterują tworzenie nie powiodło się. Na przykład w swojej `VerifyLicenseKey` funkcja elementu członkowskiego, które można wyświetlić komunikatu polu stwierdzające, że kontrolka nie może zainicjować i dlaczego.

> [!NOTE]
>  Innym sposobem dostosowania weryfikacji licencji formantu ActiveX jest sprawdzenie rejestracji bazy danych dla określonego klucza rejestru, zamiast wywoływać metodę `AfxVerifyLicFile`. Na przykład domyślna implementacja zobacz [modyfikacje plików implementacji](#_core_implementation_file_modifications) dalszej części tego artykułu.

Omówienie dodatkowe problemy z licencjonowaniem, zobacz licencjonowania problemy w [Uaktualnianie istniejącego kontrolki ActiveX](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)

