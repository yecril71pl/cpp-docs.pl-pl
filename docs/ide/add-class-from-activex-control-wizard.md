---
title: Kreator dodawania klasy z kontrolki ActiveX
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.axcontrol
helpviewer_keywords:
- ActiveX Control Wizard
- Add Class from ActiveX Control Wizard [C++]
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
ms.openlocfilehash: 736ac50f14d8434584c6f47b2953913c79b0b00a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472491"
---
# <a name="add-class-from-activex-control-wizard"></a>Kreator dodawania klasy z kontrolki ActiveX

Ten kreator umożliwia dodawanie klasy MFC z formantu ActiveX dostępne. Kreator utworzy klasę dla każdego interfejsu, który dodasz z wybranej kontrolki ActiveX.

- **Dodaj klasę**

   Określa lokalizację biblioteki typów, z którego jest tworzony klasy.

   |Opcja|Opis|
   |------------|-----------------|
   |**Registry**|Biblioteka typów jest zarejestrowany w systemie. Zarejestrowanego typu biblioteki są wymienione w **kontrolki ActiveX dostępne**.|
   |**Plik**|Biblioteka typów nie zawsze jest zarejestrowany w systemie, ale jest zawarty w pliku. Należy podać lokalizację pliku w **lokalizacji**.|

- **Dostępne kontrolki ActiveX**

   Określa formanty ActiveX w danym momencie zarejestrowany w systemie. Wybierz formant ActiveX z tej listy, aby wyświetlić swoje interfejsy w **interfejsów** listy. Zobacz [kontrolki ActiveX MFC: Dystrybucja kontrolek ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) Aby uzyskać więcej informacji na temat rejestrowania formantów ActiveX.

   Jeśli klikniesz **pliku** w obszarze **dodawania klasy z**, to pole jest niedostępna w przypadku zmiany.

- **Lokalizacja**

   Określa położenie formantu ActiveX. Jeśli klikniesz **pliku** w obszarze **dodawania klasy z**, możesz określić lokalizację pliku zawierającego bibliotekę typów. Aby przejść do lokalizacji pliku, kliknij przycisk oznaczony wielokropkiem.

   Jeśli klikniesz **rejestru** w obszarze **dodawania klasy z**, to pole jest niedostępna w przypadku zmiany.

- **Interfejsy**

   Określa interfejsy w aktualnie wybranego w formancie ActiveX **kontrolki ActiveX dostępne** lub w bibliotece typów w pliku określonego w **lokalizacji**.

   |Przycisk transferu|Opis|
   |---------------------|-----------------|
   |**>**|Dodaje interfejs aktualnie wybrany w **interfejsów** listy. Czas niedostępności, jeśli interfejs nie jest zaznaczone.|
   |**>>**|Dodaje wszystkie interfejsy w aktualnie wybranego w formancie ActiveX **kontrolki ActiveX dostępne** lub w bibliotece typów w pliku określonego w **lokalizacji**.|
   |**\<**|Usuwa klasę aktualnie wybrany w **wygenerowane klasy** listy. Czas niedostępności, jeśli klasa nie jest aktualnie wybrany w **wygenerowane klasy** listy.|
   |**\<\<**|Usuwa wszystkie klasy w **wygenerowane klasy** listy. Jeśli niedostępny **wygenerowane klasy** lista jest pusta.|

- **Wygenerowane klasy**

   Określa nazwy klas, które było generowane przy użyciu interfejsów, dodać za pomocą **>** lub **>>** przycisku. Kliknięcie tego pola Wybierz klasę, a następnie górę lub w dół klucze, aby przewijać listę, wyświetlając nazwę każdej klasy w `Class` okno i nazwę pliku w **plik .h klasy** pole, które kreator generuje po kliknięciu  **Zakończ**. Jednocześnie można wybrać tylko jedną klasę, w tym polu.

   Klasę można usunąć, wybierając ją na tej liście i klikając **<**. Nie musisz wybrać klasę w **wygenerowane klasy** pole, aby usunąć wszystkie klasy, a przez kliknięcie przycisku **<<**, Usuń wszystkie klasy w **wygenerowane klasy** pole.

- **Class**

   Określa nazwę klasy, wybranego w **wygenerowane klasy** pole, które Kreator dodaje po kliknięciu **Zakończ**. Można edytować nazwy w **klasy** pole.

- **plik .h**

   Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podane **wygenerowane klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Plik CPP**

   Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **wygenerowane klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

## <a name="see-also"></a>Zobacz też

[Dodawanie klasy z kontrolki ActiveX](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)<br>
[Klienci automatyzacji: korzystanie z bibliotek typów](../mfc/automation-clients-using-type-libraries.md)