---
title: 'Formanty MFC ActiveX: lokalizowanie formantu ActiveX'
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: a85ec5cbed797b756afd93cd8423c58d138a0625
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615422"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Formanty MFC ActiveX: lokalizowanie formantu ActiveX

W tym artykule omówiono procedury lokalizowania interfejsów kontrolek ActiveX.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

Jeśli chcesz dostosować formant ActiveX do rynku międzynarodowego, możesz chcieć zlokalizować formant. System Windows obsługuje wiele języków oprócz domyślnego języka angielskiego, w tym dla wersji niemieckiej, francuskiej i szwedzkiej. Może to spowodować problemy dla kontrolki, jeśli jej interfejs jest tylko w języku angielskim.

Ogólnie rzecz biorąc, formanty ActiveX powinny zawsze bazować na właściwościach LocaleID otaczającej. Istnieją trzy sposoby, aby to zrobić:

- Ładuj zasoby, zawsze na żądanie, na podstawie bieżącej wartości właściwości otaczającej LocaleID. Przykładowy formant ActiveX MFC [lokalizuje](../overview/visual-cpp-samples.md) używa tej strategii.

- Ładowanie zasobów przy wystąpieniu pierwszej kontrolki na podstawie właściwości otaczającej LocaleID i użycie tych zasobów dla wszystkich innych wystąpień. W tym artykule przedstawiono tę strategię.

    > [!NOTE]
    >  Nie będzie to działało prawidłowo w niektórych przypadkach, jeśli przyszłe wystąpienia mają różne ustawienia regionalne.

- Użyj `OnAmbientChanged` funkcji powiadomień, aby dynamicznie ładować odpowiednie zasoby dla ustawień regionalnych kontenera.

    > [!NOTE]
    >  Ta wartość będzie działać dla formantu, ale biblioteka DLL czasu wykonywania nie będzie dynamicznie aktualizować własnych zasobów, gdy zmieni się Właściwość otoczenia LocaleID. Ponadto biblioteki DLL w czasie wykonywania dla formantów ActiveX używają ustawień regionalnych wątków do określania ustawień regionalnych dla zasobów.

W pozostałej części tego artykułu opisano dwie metody lokalizowania. Pierwsza strategia [lokalizuje interfejs programowalności kontrolki](#_core_localizing_your_control.92.s_programmability_interface) (nazwy właściwości, metod i zdarzeń). Druga strategia [lokalizuje interfejs użytkownika formantu](#_core_localizing_the_control.92.s_user_interface)przy użyciu właściwości LocaleID otaczającej kontenera. Aby zapoznać się z pokazem lokalizacji kontroli, zobacz przykład [lokalizowanie](../overview/visual-cpp-samples.md)kontrolek ActiveX MFC.

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a>Lokalizowanie interfejsu programowalności kontrolki

Przy lokalizowaniu interfejsu programowalności formantu (interfejs używany przez programistów piszący aplikacje, które używają formantu), należy utworzyć zmodyfikowaną wersję formantu. Plik IDL (skrypt służący do tworzenia biblioteki typów formantów) dla każdego języka, który ma być obsługiwany. Jest to jedyne miejsce, w którym należy zlokalizować nazwy właściwości formantu.

Podczas tworzenia zlokalizowanej kontrolki należy uwzględnić identyfikator ustawień regionalnych jako atrybut na poziomie biblioteki typów. Na przykład, jeśli chcesz podać bibliotekę typów z nazwami zlokalizowanych właściwości francuski, Utwórz kopię PRZYKŁADu. Plik IDL i Wywołaj go SAMPLEFR. IDL. Dodaj atrybut identyfikatora ustawień regionalnych do pliku (identyfikator ustawień regionalnych dla języka francuskiego to 0x040c), podobny do następującego:

[!code-cpp[NVC_MFC_AxLoc#1](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Zmień nazwy właściwości w SAMPLEFR. Język IDL do ich odpowiedników w języku francuskim, a następnie użyj MKTYPLIB. EXE, aby utworzyć francuską bibliotekę typów, SAMPLEFR. Rejestr.

Aby utworzyć wiele zlokalizowanych bibliotek typów, można dodać dowolne zlokalizowane. Pliki IDL do projektu i zostaną skompilowane automatycznie.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Aby dodać. Plik IDL do projektu kontrolki ActiveX

1. Po otwarciu projektu kontrolki w menu **projekt** kliknij polecenie **Dodaj istniejący element**.

   Pojawi się okno dialogowe **Dodaj istniejący element** .

1. W razie potrzeby wybierz dysk i katalog do wyświetlenia.

1. W polu **Pliki typu** wybierz pozycję **wszystkie pliki ( \* . \* )**.

1. W polu listy plik kliknij dwukrotnie. Plik IDL, który ma zostać wstawiony do projektu.

1. Po dodaniu wszystkich niezbędnych czynności kliknij przycisk **Otwórz** . Pliki IDL.

Ponieważ pliki zostały dodane do projektu, zostaną skompilowane po skompilowaniu pozostałej części projektu. Zlokalizowane biblioteki typów znajdują się w bieżącym katalogu projektu kontrolki ActiveX.

W kodzie, wewnętrzne nazwy właściwości (zwykle w języku angielskim) są zawsze używane i nigdy nie są zlokalizowane. Obejmuje to mapę wysyłania formantów, funkcje wymiany właściwości i kod wymiany danych strony właściwości.

Tylko jedna biblioteka typów (. TLB) może być powiązana z zasobami implementacji kontroli (. OCX). Jest to zazwyczaj wersja z nazwami znormalizowanymi (zazwyczaj w języku angielskim). Aby dostarczyć zlokalizowaną wersję kontrolki, musisz ją dostarczyć. OCX (który został już powiązany z wartością domyślną. Wersja buforu TLB) i. Bufor TLB dla odpowiednich ustawień regionalnych. Oznacza to, że tylko. Program OCX jest wymagany w przypadku wersji angielskiej, ponieważ jest prawidłowy. Obiekt TLB został już powiązany z tym elementem. W przypadku innych ustawień regionalnych, zlokalizowana biblioteka typów musi być dostarczana z. OCX.

Aby upewnić się, że klienci formantu mogą znaleźć zlokalizowaną bibliotekę typów, należy zarejestrować specyficzne dla ustawień regionalnych. Pliki TLB w sekcji biblioteki rejestru systemu Windows. Trzeci parametr (zwykle opcjonalny) funkcji [AfxOleRegisterTypeLib](reference/registering-ole-controls.md#afxoleregistertypelib) jest dostępny do tego celu. Poniższy przykład rejestruje bibliotekę typów francuskich dla kontrolki ActiveX:

[!code-cpp[NVC_MFC_AxLoc#2](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Gdy kontrolka jest zarejestrowana, `AfxOleRegisterTypeLib` funkcja automatycznie szuka określonego. Plik TLB w tym samym katalogu co formant i rejestruje go w bazie danych rejestracji systemu Windows. Jeśli. Nie znaleziono pliku TLB, funkcja nie ma żadnego wpływu.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a>Lokalizowanie interfejsu użytkownika kontrolki

Aby zlokalizować interfejs użytkownika kontrolki, umieść wszystkie zasoby widoczne dla użytkownika (takie jak strony właściwości i komunikaty o błędach) w bibliotekach DLL zasobów specyficznych dla języka. Następnie można użyć właściwości LocaleID otaczającej kontenera, aby wybrać odpowiednią bibliotekę DLL dla ustawień regionalnych użytkownika.

Poniższy przykład kodu ilustruje jedno z podejście do lokalizowania i ładowania biblioteki DLL zasobów dla określonych ustawień regionalnych. Ta funkcja elementu członkowskiego, wywołana `GetLocalizedResourceHandle` dla tego przykładu, może być funkcją składową klasy kontrolki ActiveX:

[!code-cpp[NVC_MFC_AxLoc#3](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Należy zauważyć, że w każdym przypadku instrukcji switch można sprawdzić identyfikator podjęzyka, aby zapewnić bardziej wyspecjalizowaną lokalizację. Aby zapoznać się z prezentacją tej funkcji, zobacz w `GetResourceHandle` przykładowej funkcji formantów ActiveX [LOCALIZE](../overview/visual-cpp-samples.md)MFC.

Gdy kontrolka najpierw załaduje się do kontenera, może wywołać [COleControl:: AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid) w celu pobrania identyfikatora ustawień regionalnych. Kontrolka może następnie przekazać zwróconą wartość identyfikatora ustawień regionalnych do `GetLocalizedResourceHandle` funkcji, która ładuje właściwą bibliotekę zasobów. Kontrolka powinna przekazać wyniki dojścia, jeśli istnieje, do [AfxSetResourceHandle](reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Umieść przykład kodu powyżej w funkcji członkowskiej kontrolki, na przykład przesłonięcie elementu [COleControl:: OnSetClientSite](reference/colecontrol-class.md#onsetclientsite). Ponadto *m_hResDLL* powinna być zmienną członkowską klasy Control.

Możesz użyć podobnej logiki do lokalizowania strony właściwości kontrolki. Aby zlokalizować stronę właściwości, Dodaj kod podobny do poniższego przykładu do pliku implementacji strony właściwości (w przypadku zastąpienia elementu [COlePropertyPage:: OnSetPageSite](reference/colepropertypage-class.md#onsetpagesite)):

[!code-cpp[NVC_MFC_AxLoc#5](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
