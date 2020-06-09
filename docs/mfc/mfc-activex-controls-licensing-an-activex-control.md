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
ms.openlocfilehash: 4fe2fcf63cce02ed6c1c9943e6d0fe6ffab00a92
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622370"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX

Obsługa licencjonowania, opcjonalna funkcja formantów ActiveX, umożliwia kontrolowanie, kto może korzystać z formantu lub go rozpowszechniać. (Aby uzyskać więcej dyskusji na temat problemów z licencjonowaniem, zobacz problemy z licencjonowaniem w temacie [uaktualnianie istniejącej kontrolki ActiveX](upgrading-an-existing-activex-control.md)).

> [!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

W tym artykule omówiono następujące tematy:

- [Omówienie licencjonowania kontrolki ActiveX](#_core_overview_of_activex_control_licensing)

- [Tworzenie licencjonowanej kontroli](#_core_creating_a_licensed_control)

- [Obsługa licencjonowania](#_core_licensing_support)

- [Dostosowywanie licencjonowania kontrolki ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Kontrolki ActiveX implementujące Licencjonowanie pozwalają na określenie, jak inne osoby będą korzystać z kontrolki ActiveX. Podajesz kupującemu kontrolę z kontrolką i. Plik LIC wraz z umową, którą kupujący może dystrybuować formant, ale nie. Plik LIC, z aplikacją korzystającą z formantu. Zapobiega to zapisywaniu przez użytkowników tej aplikacji nowych aplikacji korzystających z tego formantu, bez konieczności pierwszej licencji kontroli od użytkownika.

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>Omówienie licencjonowania kontrolki ActiveX

Aby zapewnić obsługę licencjonowania dla formantów ActiveX, Klasa [COleObjectFactory](reference/coleobjectfactory-class.md) dostarcza implementację dla kilku funkcji w `IClassFactory2` interfejsie: `IClassFactory2::RequestLicKey` , `IClassFactory2::GetLicInfo` , i `IClassFactory2::CreateInstanceLic` . Gdy Deweloper aplikacji kontenera wykonuje żądanie utworzenia wystąpienia kontrolki, wywołanie `GetLicInfo` jest wykonywane w celu sprawdzenia, czy formant. Plik LIC jest obecny. Jeśli formant jest licencjonowany, wystąpienie kontrolki można utworzyć i umieścić w kontenerze. Po zakończeniu konstruowania przez dewelopera aplikacji kontenera inne wywołanie funkcji `RequestLicKey` jest wykonywane. Ta funkcja zwraca klucz licencji (prosty ciąg znaków) do aplikacji kontenera. Zwrócony klucz jest następnie osadzony w aplikacji.

Na poniższym rysunku przedstawiono weryfikację licencji kontrolki ActiveX, która będzie używana podczas opracowywania aplikacji kontenera. Jak wspomniano wcześniej, Deweloper aplikacji kontenera musi mieć odpowiednie. Plik LIC został zainstalowany na komputerze deweloperskim w celu utworzenia wystąpienia formantu.

![Licencjonowane kontrolki ActiveX zweryfikowane podczas opracowywania](../mfc/media/vc374d1.gif "Licencjonowane kontrolki ActiveX zweryfikowane podczas opracowywania") <br/>
Weryfikacja licencjonowanej kontrolki ActiveX podczas tworzenia

Następny proces przedstawiony na poniższej ilustracji występuje, gdy użytkownik końcowy uruchamia aplikację kontenera.

Gdy aplikacja jest uruchomiona, wystąpienie formantu zwykle musi zostać utworzone. W tym celu kontener wykonuje wywołanie `CreateInstanceLic` , przekazując osadzony klucz licencji jako parametr. Następnie zostanie wykonane porównanie ciągów między osadzonym kluczem licencji i własną kopią klucza licencji formantu. Jeśli dopasowanie zakończyło się pomyślnie, wystąpienie formantu zostanie utworzone i aplikacja będzie nadal działać normalnie. Należy pamiętać, że. Plik LIC nie musi być obecny na komputerze użytkownika kontroli.

![Licencjonowany formant ActiveX zweryfikowany podczas wykonywania](../mfc/media/vc374d2.gif "Licencjonowany formant ActiveX zweryfikowany podczas wykonywania") <br/>
Weryfikacja licencjonowanego formantu ActiveX podczas wykonywania

Licencjonowanie kontroli obejmuje dwa podstawowe składniki: konkretny kod w bibliotece DLL implementacji kontroli i plik licencji. Kod składa się z dwóch (lub prawdopodobnie trzech) wywołań funkcji i ciągu znaków, zwanego dalej "ciągiem licencji" zawierającym informacje o prawach autorskich. Te wywołania i ciąg licencji są Znalezione w implementacji kontroli (. CPP). Plik licencji generowany przez kreatora kontrolek ActiveX jest plikiem tekstowym z instrukcją praw autorskich. Nazwa jest używana przy użyciu nazwy projektu. Rozszerzenie LIC, np. przykład. LIC. Jeśli jest wymagane użycie czasu projektowania, do licencjonowanej kontroli musi być dołączony plik licencji.

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>Tworzenie licencjonowanej kontroli

W przypadku tworzenia struktury kontroli przy użyciu kreatora kontrolek ActiveX można łatwo włączyć obsługę licencjonowania. Po określeniu, że formant powinien mieć licencję w czasie wykonywania, Kreator kontrolki ActiveX dodaje kod do klasy kontrolki do obsługi licencjonowania. Kod składa się z funkcji, które używają klucza i pliku licencji do weryfikacji licencji. Te funkcje mogą być również modyfikowane w celu dostosowania licencjonowania kontroli. Aby uzyskać więcej informacji na temat dostosowywania licencji, zobacz [Dostosowywanie licencjonowania kontrolki ActiveX](#_core_customizing_the_licensing_of_an_activex_control) w dalszej części tego artykułu.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Aby dodać obsługę licencjonowania za pomocą Kreatora kontrolki ActiveX podczas tworzenia projektu kontrolki

1. Skorzystaj z instrukcji przedstawionych w temacie [Tworzenie kontrolki ActiveX MFC](reference/creating-an-mfc-activex-control.md). Strona **Ustawienia aplikacji** w Kreatorze kontrolki ActiveX zawiera opcję tworzenia kontrolki z licencją czasu wykonywania.

Kreator kontrolek ActiveX generuje teraz strukturę kontrolek ActiveX, która obejmuje podstawową obsługę licencjonowania. Szczegółowe wyjaśnienie kodu licencji można znaleźć w następnym temacie.

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>Obsługa licencjonowania

W przypadku dodawania obsługi licencjonowania do kontrolki ActiveX przy użyciu kreatora kontrolek ActiveX, Kreator kontrolek ActiveX dodaje kod, który deklaruje i implementuje możliwość licencjonowania, jest dodawany do nagłówka i plików implementacji formantu. Ten kod składa się z `VerifyUserLicense` funkcji składowej i `GetLicenseKey` funkcji członkowskiej, która zastępuje implementacje domyślne Znalezione w [COleObjectFactory](reference/coleobjectfactory-class.md) . Te funkcje pobierają i weryfikują licencję kontroli.

> [!NOTE]
> Trzecia funkcja członkowska `VerifyLicenseKey` nie jest generowana przez kreatora kontrolek ActiveX, ale można ją zastąpić, aby dostosować zachowanie weryfikacji klucza licencji.

Te funkcje składowe są następujące:

- [VerifyUserLicense](reference/coleobjectfactory-class.md#verifyuserlicense)

   Sprawdza, czy formant zezwala na użycie w czasie projektowania, sprawdzając system pod kątem obecności pliku licencji kontroli. Ta funkcja jest wywoływana przez platformę w ramach przetwarzania `IClassFactory2::GetLicInfo` i `IClassFactory::CreateInstanceLic` .

- [GetLicenseKey](reference/coleobjectfactory-class.md#getlicensekey)

   Żąda unikatowego klucza z biblioteki DLL kontrolki. Ten klucz jest osadzony w aplikacji kontenera i używany później, w połączeniu z `VerifyLicenseKey` , do tworzenia wystąpienia formantu. Ta funkcja jest wywoływana przez platformę w ramach przetwarzania `IClassFactory2::RequestLicKey` .

- [VerifyLicenseKey](reference/coleobjectfactory-class.md#verifylicensekey)

   Sprawdza, czy klucz osadzony i unikatowy klucz kontrolki są takie same. Dzięki temu kontener może utworzyć wystąpienie kontrolki do użycia. Ta funkcja jest wywoływana przez platformę w ramach przetwarzania `IClassFactory2::CreateInstanceLic` i można ją zastąpić, aby zapewnić dostosowaną weryfikację klucza licencji. Implementacja domyślna wykonuje porównanie ciągów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie licencjonowania kontrolki ActiveX](#_core_customizing_the_licensing_of_an_activex_control)w dalszej części tego artykułu.

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>Modyfikacje pliku nagłówka

Kreator kontrolek ActiveX umieszcza w pliku nagłówkowym formantu następujący kod. W tym przykładzie są zadeklarowane dwie funkcje składowe `CSampleCtrl` obiektu `factory` , które sprawdza obecność formantu. Plik LIC i inny, który pobiera klucz licencji do użycia w aplikacji zawierającej formant:

[!code-cpp[NVC_MFC_AxUI#39](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>Modyfikacje pliku implementacji

Kreator kontrolek ActiveX umieszcza następujące dwie instrukcje w pliku implementacji kontroli, aby zadeklarować nazwę pliku licencji i ciąg licencji:

[!code-cpp[NVC_MFC_AxUI#40](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> W przypadku modyfikacji `szLicString` w dowolny sposób należy również zmodyfikować pierwszy wiersz w kontrolce. Plik LIC lub Licencjonowanie nie będzie działać prawidłowo.

Kreator kontrolek ActiveX umieszcza następujący kod w pliku implementacji kontroli w celu zdefiniowania klasy formantów `VerifyUserLicense` i `GetLicenseKey` funkcji:

[!code-cpp[NVC_MFC_AxUI#41](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Na koniec **Kreator kontrolki ActiveX** modyfikuje projekt kontrolki. Plik IDL. Słowo kluczowe **licencjonowane** jest dodawane do deklaracji coclass formantu, jak w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxUI#42](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>Dostosowywanie licencjonowania kontrolki ActiveX

Ponieważ `VerifyUserLicense` , `GetLicenseKey` i `VerifyLicenseKey` są zadeklarowane jako wirtualne funkcje członkowskie klasy fabryki kontroli, można dostosować zachowanie licencjonowania kontroli.

Na przykład możesz zapewnić kilka poziomów licencjonowania dla kontrolki, zastępując `VerifyUserLicense` `VerifyLicenseKey` funkcje elementu członkowskiego lub. Wewnątrz tej funkcji można dostosować, które właściwości lub metody są dostępne dla użytkownika zgodnie z wykrytym poziomem licencji.

Można również dodać kod do `VerifyLicenseKey` funkcji, która dostarcza dostosowanej metody do informowania użytkownika, że tworzenie kontroli nie powiodło się. Na przykład, w `VerifyLicenseKey` funkcji składowej można wyświetlić okno komunikatu z informacją o tym, że nie można zainicjować formantu i dlaczego.

> [!NOTE]
> Innym sposobem dostosowania weryfikacji licencji kontrolki ActiveX jest sprawdzenie bazy danych rejestracji dla określonego klucza rejestru zamiast wywołania `AfxVerifyLicFile` . Przykład implementacji domyślnej można znaleźć w sekcji [modyfikacje pliku implementacji](#_core_implementation_file_modifications) w tym artykule.

Aby uzyskać więcej dyskusji na temat problemów z licencjonowaniem, zobacz problemy z licencjonowaniem w temacie [uaktualnianie istniejącej kontrolki ActiveX](upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kreator kontrolek ActiveX MFC](reference/mfc-activex-control-wizard.md)
