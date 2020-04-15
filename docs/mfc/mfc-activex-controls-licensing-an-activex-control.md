---
title: 'Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX'
ms.date: 11/19/2018
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: aaab4ae3bb13790784a66d53b41dbc3a7cdaec89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364603"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX

Obsługa licencjonowania, opcjonalna funkcja formantów ActiveX, pozwala kontrolować, kto może używać lub rozpowszechniać formantu. (Aby uzyskać dodatkowe omówienie problemów z licencjonowaniem, zobacz Problemy z licencjonowaniem [w uaktualnianiu istniejącego formantu ActiveX).](../mfc/upgrading-an-existing-activex-control.md)

> [!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

W tym artykule omówiono następujące tematy:

- [Omówienie licencjonowania activex control](#_core_overview_of_activex_control_licensing)

- [Tworzenie licencjonowanej formantu](#_core_creating_a_licensed_control)

- [Pomoc techniczna w udzielaniu licencji](#_core_licensing_support)

- [Dostosowywanie licencjonowania formantu ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

ActiveX formanty, które implementują licencjonowanie pozwalają, jako deweloper formantu, aby określić, jak inne osoby będą używać formantu ActiveX. Użytkownik przekazuje kupującemu kontrolę z kontrolą i . LIC, z umową, że nabywca może rozpowszechniać formant, ale nie . LIC, z aplikacją, która używa formantu. Uniemożliwia to użytkownikom tej aplikacji pisanie nowych aplikacji, które używają formantu, bez uprzedniego licencjonowania formantu od ciebie.

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>Omówienie licencjonowania activex control

Aby zapewnić obsługę licencjonowania formantów ActiveX, klasa [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) `IClassFactory2` zapewnia `IClassFactory2::RequestLicKey`implementację dla kilku funkcji w interfejsie: , `IClassFactory2::GetLicInfo`i `IClassFactory2::CreateInstanceLic`. Gdy deweloper aplikacji kontenera sprawia, że żądanie utworzenia `GetLicInfo` wystąpienia formantu, wywołanie jest wywoływane w celu sprawdzenia, czy formant . LIC jest obecny. Jeśli formant jest licencjonowany, można utworzyć i umieścić w kontenerze wystąpienie formantu. Po zakończeniu konstruowania aplikacji kontenera, kolejne wywołanie `RequestLicKey`funkcji, tym razem do , jest dokonywane. Ta funkcja zwraca klucz licencyjny (ciąg znaków prostych) do aplikacji kontenera. Zwrócony klucz jest następnie osadzony w aplikacji.

Poniższy rysunek przedstawia weryfikację licencji formantu ActiveX, który będzie używany podczas tworzenia aplikacji kontenera. Jak wspomniano wcześniej, deweloper aplikacji kontenera musi mieć odpowiednie . LIC zainstalowany na komputerze deweloperskim, aby utworzyć wystąpienie formantu.

![Licencjonowany sterownik ActiveX zweryfikowany przy opracowywaniu](../mfc/media/vc374d1.gif "Licencjonowany sterownik ActiveX zweryfikowany przy opracowywaniu") <br/>
Weryfikacja licencjonowanego sterownika ActiveX podczas opracowywania

Następny proces, pokazany na poniższym rysunku, występuje, gdy użytkownik końcowy uruchamia aplikację kontenera.

Po uruchomieniu aplikacji zwykle należy utworzyć wystąpienie formantu. Kontener realizuje to, wywołując `CreateInstanceLic`, przekazując osadzony klucz licencyjny jako parametr. Porównanie ciągów jest następnie dokonywane między osadzonym kluczem licencyjnym a własną kopią klucza licencyjnego formantu. Jeśli dopasowanie zakończy się pomyślnie, zostanie utworzone wystąpienie formantu i aplikacja będzie nadal wykonywana normalnie. Należy pamiętać, że . LIC nie musi znajdować się na komputerze użytkownika sterującego.

![Licencjonowany formant ActiveX zweryfikowany podczas wykonywania](../mfc/media/vc374d2.gif "Licencjonowany formant ActiveX zweryfikowany podczas wykonywania") <br/>
Weryfikacja licencjonowanego formantu ActiveX podczas wykonywania

Licencjonowanie kontroli składa się z dwóch podstawowych składników: określonego kodu w implementacji dll formantu i pliku licencji. Kod składa się z dwóch (lub ewentualnie trzech) wywołań funkcji i ciągu znaków, zwanego dalej "ciągiem licencyjnym", zawierającego powiadomienie o prawach autorskich. Te wywołania i ciąg licencji znajdują się w implementacji formantu (. CPP). Plik licencji, wygenerowany przez Kreatora sterowania ActiveX, jest plikiem tekstowym z oświadczeniem o prawach autorskich. Nazwa nosi nazwę projektu z programem . rozszerzenie LIC, na przykład SAMPLE. Lic. Licencjonowanemu formancie musi towarzyszyć plik licencji, jeśli potrzebne jest użycie w czasie projektowania.

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>Tworzenie licencjonowanej formantu

Korzystając z Kreatora kontroli ActiveX do utworzenia struktury sterowania, łatwo jest dołączyć obsługę licencjonowania. Po określeniu, że formant powinien mieć licencję w czasie wykonywania, Kreator kontroli ActiveX dodaje kod do klasy formantu do obsługi licencjonowania. Kod składa się z funkcji, które używają klucza i pliku licencji do weryfikacji licencji. Te funkcje można również zmodyfikować, aby dostosować licencjonowanie kontroli. Aby uzyskać więcej informacji na temat dostosowywania licencji, zobacz [Dostosowywanie licencjonowania formantu ActiveX](#_core_customizing_the_licensing_of_an_activex_control) w dalszej części tego artykułu.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Aby dodać obsługę licencjonowania za pomocą Kreatora sterowania ActiveX podczas tworzenia projektu sterowania

1. Użyj instrukcji tworzenia [formantu MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control.md). **Strona Ustawienia aplikacji** Kreatora sterowania ActiveX zawiera opcję tworzenia formantu z licencją wył.

Kreator kontroli ActiveX generuje teraz platformę sterowania ActiveX, która zawiera podstawową obsługę licencjonowania. Szczegółowe informacje na temat kodu licencjonowania można znaleźć w następnym temacie.

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>Pomoc techniczna w udzielaniu licencji

Korzystając z Kreatora kontroli ActiveX, aby dodać obsługę licencjonowania do formantu ActiveX, Kreator kontroli ActiveX dodaje kod, który deklaruje i implementuje możliwości licencjonowania jest dodawany do nagłówka formantu i plików implementacji. Ten kod składa `VerifyUserLicense` się z `GetLicenseKey` funkcji elementu członkowskiego i funkcji elementu członkowskiego, które zastępują domyślne implementacje znalezione w [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Te funkcje pobierają i weryfikują licencję kontrolną.

> [!NOTE]
> Funkcja trzeciego elementu `VerifyLicenseKey` członkowskiego nie jest generowana przez Kreatora sterowania ActiveX, ale może zostać zastąpiona w celu dostosowania zachowania weryfikacji klucza licencyjnego.

Te funkcje członkowskie są następujące:

- [VerifyUserLicense (Weryfikujuskowanie licencji)](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Sprawdza, czy formant umożliwia użycie w czasie projektowania, sprawdzając system pod kątem obecności pliku licencji kontrolnej. Ta funkcja jest wywoływana przez `IClassFactory2::GetLicInfo` ramy `IClassFactory::CreateInstanceLic`w ramach przetwarzania i .

- [Klucz GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Żąda unikatowego klucza z biblioteki DLL formantu. Ten klucz jest osadzony w aplikacji kontenera `VerifyLicenseKey`i używany później, w połączeniu z , aby utworzyć wystąpienie formantu. Ta funkcja jest wywoływana przez `IClassFactory2::RequestLicKey`platformę w ramach przetwarzania .

- [Verifylicensekey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Sprawdza, czy klucz osadzony i unikatowy klucz formantu są takie same. Dzięki temu kontener, aby utworzyć wystąpienie formantu dla jego użycia. Ta funkcja jest wywoływana przez `IClassFactory2::CreateInstanceLic` platformę jako część przetwarzania i może zostać zastąpiona w celu zapewnienia dostosowanej weryfikacji klucza licencyjnego. Domyślna implementacja wykonuje porównanie ciągów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie licencjonowania formantu ActiveX](#_core_customizing_the_licensing_of_an_activex_control)w dalszej części tego artykułu.

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>Modyfikacje pliku nagłówka

Kreator sterowania ActiveX umieszcza następujący kod w pliku nagłówka formantu. W tym przykładzie dwie `CSampleCtrl`funkcje `factory` członkowskie obiektu 's są zadeklarowane, jeden, który weryfikuje obecność formantu . LIC i inny, który pobiera klucz licencyjny do użycia w aplikacji zawierającej formant:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>Modyfikacje pliku implementacji

Kreator sterowania ActiveX umieszcza następujące dwie instrukcje w pliku implementacji formantu w celu zadeklarowania nazwy pliku licencji i ciągu licencji:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> Jeśli zmodyfikujesz `szLicString` w jakikolwiek sposób, należy również zmodyfikować pierwszy wiersz w formancie . LIC nie będzie działać poprawnie.

Kreator sterowania ActiveX umieszcza następujący kod w pliku implementacji `VerifyUserLicense` formantu w celu zdefiniowania klasy kontroli i `GetLicenseKey` funkcji:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Na koniec **Kreator sterowania ActiveX** modyfikuje projekt sterowania . IDL. **Licencjonowane** słowo kluczowe jest dodawane do deklaracji coclass formantu, jak w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>Dostosowywanie licencjonowania formantu ActiveX

Ponieważ `VerifyUserLicense` `GetLicenseKey`, `VerifyLicenseKey` i są zadeklarowane jako wirtualne funkcje członkowskie klasy fabryki sterowania, można dostosować zachowanie licencjonowania formantu.

Na przykład można podać kilka poziomów licencjonowania formantu, `VerifyUserLicense` `VerifyLicenseKey` zastępując funkcje lub element członkowski. Wewnątrz tej funkcji można dostosować, które właściwości lub metody są narażone na użytkownika zgodnie z poziomem licencji, który został wykryty.

Można również dodać kod `VerifyLicenseKey` do funkcji, która zapewnia dostosowaną metodę informowania użytkownika, że tworzenie formantu nie powiodło się. Na przykład w `VerifyLicenseKey` funkcji elementu członkowskiego można wyświetlić okno komunikatu z informacją, że formant nie można zainicjować i dlaczego.

> [!NOTE]
> Innym sposobem dostosowania weryfikacji licencji kontroli ActiveX jest sprawdzenie bazy danych rejestracji dla `AfxVerifyLicFile`określonego klucza rejestru, zamiast wywoływania . Na przykład domyślnej implementacji zobacz [implementacji modyfikacji pliku](#_core_implementation_file_modifications) sekcji tego artykułu.

Aby zapoznać się z dodatkowymi omówieniami problemów z licencjonowaniem, zobacz Problemy z licencjonowaniem [w uaktualnianiu istniejącego formantu ActiveX](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)
