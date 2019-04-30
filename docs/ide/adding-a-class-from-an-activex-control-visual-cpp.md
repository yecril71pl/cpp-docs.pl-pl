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
ms.openlocfilehash: 1d91d98082a5c5d6d45bfa31e81c59e8925aa2c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386278"
---
# <a name="add-a-class-from-an-activex-control"></a>Dodawanie klasy z kontrolki ActiveX

Ten kreator umożliwia tworzenie klasy MFC z interfejsu, dostępne kontrolki ActiveX. Można dodać klasy MFC do [aplikacji MFC](../mfc/reference/creating-an-mfc-application.md), [biblioteki MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md), lub [kontrolki MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control.md).

> [!WARNING]
> W programie Visual Studio 2017 w wersji 15.9 Microsoft wycofała tego kreatora kodu, a zostanie on usunięty w przyszłych wersjach programu Visual Studio. Ten kreator jest rzadko używana. Ogólna obsługa biblioteki ATL i MFC nie jest wpływ usunięcia tego kreatora. Jeśli chcesz przekazać opinię dotyczącą tego wycofywania, wykonaj [w ramach tej ankiety](https://www.surveymonkey.com/r/QDWKKCN). Twoja opinia ma znaczenie dla nas.
<!-- Blank comment here to separate the warning and note. -->
> [!NOTE]
> Nie potrzebujesz do tworzenia projektu MFC przy użyciu usługi Automation, możliwość dodawania klasy z kontrolki ActiveX.

Kontrolki ActiveX jest składnik oprogramowania wielokrotnego użytku, oparte na Component Object Model (COM), który obsługuje szeroki zakres funkcji OLE. Ten można dostosować do potrzeb wiele oprogramowania. Można użyć kontrolek ActiveX w zwykłych kontenery kontrolek ActiveX lub w Internecie w strony sieci Web.

**Dodawanie klasy MFC z formantu ActiveX:**

1. W obu **Eksploratora rozwiązań** lub [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać klasy kontrolki ActiveX.

1. Z menu skrótów wybierz polecenie **Dodaj**, a następnie wybierz **Dodaj klasę**.

1. W [Dodaj klasę](../ide/add-class-dialog-box.md) okno dialogowe, **szablony** okienku wybierz **klasy MFC z formantu ActiveX**, a następnie wybierz **Otwórz** do wyświetlenia [dodawania klasy z Kreatora kontrolek ActiveX](#add-class-from-activex-control-wizard).

W kreatorze możesz dodać więcej niż jeden interfejs w kontrolce ActiveX. Można również tworzyć klasy z więcej niż jeden formant ActiveX, w jednej sesji kreatora.

Można dodać klasy z kontrolki ActiveX zarejestrowany w systemie, lub można dodać klasy z kontrolki ActiveX na terenie typów plików biblioteki (.tlb, .olb, .dll, .ocx lub .exe) bez rejestrowania ich pierwszy w systemie. Aby uzyskać więcej informacji na temat rejestrowanie kontrolek ActiveX zobacz [kontroluje rejestrowanie OLE](../mfc/reference/registering-ole-controls.md).

Kreator utworzy klasę MFC pochodną [CWnd](../mfc/reference/cwnd-class.md) lub [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), dla każdego interfejsu, możesz dodać z wybranej kontrolki ActiveX.

## <a name="in-this-section"></a>W tej sekcji

- [Dodawanie klasy z Kreatora kontrolek ActiveX](#add-class-from-activex-control-wizard)

## <a name="add-class-from-activex-control-wizard"></a>Dodawanie klasy z Kreatora kontrolek ActiveX

Ten kreator umożliwia dodawanie klasy MFC z formantu ActiveX dostępne. Kreator utworzy klasę dla każdego interfejsu, który dodasz z wybranej kontrolki ActiveX.

- **Dodaj klasę**

  Określa lokalizację biblioteki typów, z którego jest tworzony klasy.

  |Opcja|Opis|
  |------------|-----------------|
  |**Registry**|Biblioteka typów jest zarejestrowany w systemie. Zarejestrowanego typu biblioteki są wymienione w **kontrolki ActiveX dostępne**.|
  |**Plik**|Biblioteka typów musi być zarejestrowane w systemie, ale są przechowywane w pliku. Podaj lokalizację plików w programie **lokalizacji**.|

- **Dostępne kontrolki ActiveX**

  Określa formanty ActiveX w danym momencie zarejestrowany w systemie. Wybierz formant ActiveX z tej listy, aby wyświetlić swoje interfejsy w **interfejsów** listy. Zobacz [kontrolki MFC ActiveX: Dystrybucja kontrolek ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) Aby uzyskać więcej informacji na temat rejestrowania formantów ActiveX.

  Jeśli wybierzesz **pliku** w obszarze **dodawania klasy z**, to pole jest niedostępna w przypadku zmiany.

- **Lokalizacja**

  Określa położenie formantu ActiveX. Jeśli wybierzesz **pliku** w obszarze **dodawania klasy z**, możesz określić lokalizację pliku, który zawiera biblioteki typów. Aby przejść do lokalizacji pliku, wybierz przycisk wielokropka.

  Jeśli wybierzesz **rejestru** w obszarze **dodawania klasy z**, to pole jest niedostępna w przypadku zmiany.

- **Interfejsy**

  Określa interfejsy w formancie ActiveX. Kreator używa interfejsów z bieżącego zaznaczenia w **kontrolki ActiveX dostępne**, lub wykorzystuje interfejsy z pliku biblioteki typów, które są określone w **lokalizacji**.

  |Przycisk transferu|Opis|
  |---------------------|-----------------|
  |**>**|Dodaje interfejs aktualnie wybrany w **interfejsów** listy. Czas niedostępności, jeśli interfejs nie jest zaznaczone.|
  |**>>**|Dodaje wszystkie interfejsy w formancie ActiveX. Kreator używa interfejsów z bieżącego zaznaczenia w **kontrolki ActiveX dostępne**, lub wykorzystuje interfejsy z pliku biblioteki typów, które są określone w **lokalizacji**.|
  |**\<**|Usuwa klasę aktualnie wybrany w **wygenerowane klasy** listy. Czas niedostępności, jeśli klasa nie jest aktualnie wybrany w **wygenerowane klasy** listy.|
  |**\<\<**|Usuwa wszystkie klasy w **wygenerowane klasy** listy. Jeśli niedostępny **wygenerowane klasy** lista jest pusta.|

- **Wygenerowane klasy**

  Określa nazwy klas, które było generowane przy użyciu interfejsów, dodać za pomocą **>** lub **>>** przycisku. Można wybrać tego pola Wybierz klasę, a następnie górę lub w dół klucze, aby przewijać listę. Po wybraniu **Zakończ**, może wyświetlić nazwy wygenerowanej klasy w **klasy** pole i każdy wygenerowany plik nazwy **plik .h klasy** pole. Jednocześnie można wybrać tylko jedną klasę, w tym polu.

  Klasę można usunąć, wybierając ją na tej liście, a następnie wybierając **<**. Nie potrzebujesz wybrać klasę w **wygenerowane klasy** pole, aby usunąć wszystkie klasy. Wybierając **<<**, Usuń wszystkie klasy w **wygenerowane klasy** pole.

- **Class**

   Określa nazwę klasy, wybranego w **wygenerowane klasy** pole, które Kreator dodaje po wybraniu **Zakończ**. Można edytować nazwy w **klasy** pole.

- **plik .h**

  Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podane **wygenerowane klasy**. Wybierz przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli istniejący plik, Kreator nie Zapisz go w wybranej lokalizacji do momentu wybierz **Zakończ** w kreatorze.

  Kreator nie zastępuje pliku. Jeśli wybierz nazwę istniejącego pliku, a następnie wybierz pozycję **Zakończ**, Kreator wyświetli monit o wskazuje, czy należy dołączyć deklaracji klasy zawartości pliku. Wybierz **tak** można dołączyć pliku; wybierz **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Plik CPP**

  Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **wygenerowane klasy**. Wybierz przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie wybierzesz **Zakończ** w kreatorze.

  Kreator nie zastępuje pliku. Jeśli wybierz nazwę istniejącego pliku, a następnie wybierz pozycję **Zakończ**, Kreator wyświetli monit o wskazuje, czy należy dołączyć Implementacja klasy zawartości pliku. Wybierz **tak** można dołączyć pliku; wybierz **nie** aby powrócić do kreatora i podaj inną nazwę pliku.
