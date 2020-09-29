---
title: Dodawanie klasy z kontrolki ActiveX
ms.date: 11/08/2018
f1_keywords:
- vc.codewiz.class.axcontrol
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
- ActiveX Control Wizard
- add class from ActiveX control wizard [C++]
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
ms.openlocfilehash: d63f73e17e47f2cabb8f1a55c71325ec7068a2c8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500377"
---
# <a name="add-a-class-from-an-activex-control"></a>Dodawanie klasy z kontrolki ActiveX

Ten Kreator służy do tworzenia klasy MFC z interfejsu w dostępnej kontrolce ActiveX. Można dodać klasę MFC do [aplikacji MFC](../mfc/reference/creating-an-mfc-application.md), [biblioteki MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md)lub [kontrolki ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md).

> [!WARNING]
> W programie Visual Studio 2017 w wersji 15,9 Firma Microsoft zaprzestarzało ten Kreator kodu, a my usuniemy go w przyszłej wersji programu Visual Studio. Ten Kreator jest rzadko używany. Usunięcie tego kreatora nie ma wpływu na ogólne wsparcie dla ATL i MFC. Jeśli chcesz podzielić swoją opinię na temat tego wycofania, Ukończ [tę ankietę](https://www.surveymonkey.com/r/QDWKKCN). Twoja opinia jest dla nas ważna.
<!-- Blank comment here to separate the warning and note. -->
> [!NOTE]
> Nie musisz tworzyć projektu MFC z włączonym automatyzacją, aby dodać klasę z kontrolki ActiveX.

Kontrolka ActiveX to składnik oprogramowania wielokrotnego użytku oparty na Component Object Model (COM), który obsługuje szeroką gamę funkcji OLE. Można je dostosować do potrzeb wielu programów. Kontrolki ActiveX można używać w zwykłych kontenerach formantów ActiveX lub w Internecie na World Wide Web stronach.

**Aby dodać klasę MFC z kontrolki ActiveX:**

1. W **Eksplorator rozwiązań** lub [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać klasę kontrolki ActiveX.

1. Z menu skrótów wybierz polecenie **Dodaj**, a następnie wybierz polecenie **Dodaj klasę**.

1. W oknie dialogowym [Dodawanie klasy](./adding-a-class-visual-cpp.md#add-class-dialog-box) w okienku **Szablony** wybierz pozycję **Klasa MFC z kontrolki ActiveX**, a następnie wybierz pozycję **Otwórz** , aby wyświetlić [Kreatora dodawania klasy z formantu ActiveX](#add-class-from-activex-control-wizard).

W kreatorze można dodać więcej niż jeden interfejs w kontrolce ActiveX. Można również tworzyć klasy z więcej niż jednej kontrolki ActiveX w pojedynczej sesji kreatora.

Można dodać klasy z kontrolek ActiveX zarejestrowanych w systemie lub dodać klasy z formantów ActiveX znajdujących się w plikach biblioteki typów (TLB,. olb,. dll,. ocx lub. exe) bez wcześniejszego rejestrowania ich w systemie. Aby uzyskać więcej informacji na temat rejestrowania formantów ActiveX, zobacz [Rejestrowanie formantów OLE](../mfc/reference/registering-ole-controls.md).

Kreator tworzy klasę MFC, pochodną od [CWnd](../mfc/reference/cwnd-class.md) lub z [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), dla każdego dodawanego interfejsu z wybranej kontrolki ActiveX.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator dodawania klasy z kontrolki ActiveX](#add-class-from-activex-control-wizard)

## <a name="add-class-from-activex-control-wizard"></a>Kreator dodawania klasy z kontrolki ActiveX

Użyj tego kreatora, aby dodać klasę MFC z dostępnej kontrolki ActiveX. Kreator tworzy klasę dla każdego interfejsu dodawanego z wybranej kontrolki ActiveX.

- **Dodaj klasę z**

  Określa lokalizację biblioteki typów, z której zostanie utworzona klasa.

  |Opcja|Opis|
  |------------|-----------------|
  |**Rejestr**|Biblioteka typów jest zarejestrowana w systemie. Zarejestrowane biblioteki typów są wymienione w **dostępnych kontrolkach ActiveX**.|
  |**Plik**|Biblioteka typów nie musi być zarejestrowana w systemie, ale jest przechowywana w pliku. Podaj lokalizację pliku w **lokalizacji**.|

- **Dostępne kontrolki ActiveX**

  Określa kontrolki ActiveX aktualnie zarejestrowane w systemie. Wybierz formant ActiveX z tej listy, aby wyświetlić jego interfejsy na liście **interfejsy** . Zobacz [kontrolki ActiveX MFC: dystrybucja](../mfc/mfc-activex-controls-distributing-activex-controls.md) kontrolek ActiveX, aby uzyskać więcej informacji na temat rejestrowania formantów ActiveX.

  Jeśli wybierzesz opcję **plik** w obszarze **Dodaj klasę z**, to pole jest niedostępne do zmiany.

- **Lokalizacja**

  Określa lokalizację kontrolki ActiveX. Jeśli wybierzesz opcję **plik** w obszarze **Dodaj klasę z**, możesz podać lokalizację pliku, który ma bibliotekę typów. Aby przejść do lokalizacji pliku, wybierz przycisk wielokropka.

  Jeśli wybierzesz pozycję **Rejestr** w obszarze **Dodawanie klasy z**, to pole jest niedostępne do zmiany.

- **Interfejsy**

  Określa interfejsy w kontrolce ActiveX. Kreator używa interfejsów z bieżącego wyboru w **dostępnych kontrolkach ActiveX**lub używa interfejsów z pliku biblioteki typów określonego w **lokalizacji**.

  |Przycisk transferu|Opis|
  |---------------------|-----------------|
  |**>**|Dodaje interfejs aktualnie wybrany na liście **interfejsy** . Niedostępne, jeśli nie wybrano interfejsu.|
  |**>>**|Dodaje wszystkie interfejsy w kontrolce ActiveX. Kreator używa interfejsów z bieżącego wyboru w **dostępnych kontrolkach ActiveX**lub używa interfejsów z pliku biblioteki typów określonego w **lokalizacji**.|
  |**\<**|Usuwa klasę aktualnie wybraną z listy **wygenerowanych klas** . Niedostępne, jeśli żadna Klasa nie jest obecnie zaznaczona na liście **wygenerowanych klas** .|
  |**\<\<**|Usuwa wszystkie klasy z listy **wygenerowanych klas** . Niedostępne, jeśli lista **wygenerowanych klas** jest pusta.|

- **Wygenerowane klasy**

  Określa nazwy klas do wygenerowania z interfejsów dodanych za pomocą **>** przycisku lub **>>** . Możesz zaznaczyć to pole, aby wybrać klasę, a następnie użyć klawiszy w górę lub w dół, aby przewijać listę. Po wybraniu przycisku **Zakończ**można wyświetlić każdą wygenerowaną nazwę klasy w polu **Klasa** i każdą wygenerowaną nazwę pliku w polu **plik. h** . W tym polu można wybrać tylko jedną klasę naraz.

  Możesz usunąć klasę, wybierając ją na liście i wybierając **<** . Nie musisz wybierać klasy w polu **wygenerowane klasy** , aby usunąć wszystkie klasy. Zaznaczając **<<** , należy usunąć wszystkie klasy w polu **wygenerowane klasy** .

- **Klasa**

   Określa nazwę klasy wybranej w polu **wygenerowane klasy** , którą Kreator dodaje po wybraniu przycisku **Zakończ**. Nazwę można edytować w polu Class ( **Klasa** ).

- **plik h**

  Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie dostarczanej w **wygenerowanych klasach**. Wybierz przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji, lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji, dopóki nie zostanie wybrana opcja **Zakończ** w kreatorze.

  Kreator nie zastąpi pliku. Jeśli wybierzesz nazwę istniejącego pliku, a następnie wybierzesz przycisk **Zakończ**, Kreator poprosi o wskazanie, czy dołączać deklarację klasy do zawartości pliku. Wybierz pozycję **tak** , aby dołączyć plik; Wybierz pozycję **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **plik. cpp**

  Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie dostarczanej w **wygenerowanych klasach**. Wybierz przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie zostanie wybrana opcja **Zakończ** w kreatorze.

  Kreator nie zastąpi pliku. Jeśli wybierzesz nazwę istniejącego pliku, a następnie wybierzesz przycisk **Zakończ**, Kreator poprosi o wskazanie, czy dołączać implementację klasy do zawartości pliku. Wybierz pozycję **tak** , aby dołączyć plik; Wybierz pozycję **nie** , aby powrócić do kreatora i określić inną nazwę pliku.
