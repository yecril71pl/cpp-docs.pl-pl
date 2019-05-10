---
title: Kreator dodawania klasy z biblioteki typów
ms.date: 05/09/2019
helpviewer_keywords:
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
ms.openlocfilehash: 794df6c207c2f2e93cdcc63a6b83cd3434764e87
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525472"
---
# <a name="add-class-from-typelib-wizard"></a>Kreator dodawania klasy z biblioteki typów

::: moniker range="vs-2019"

Ten kreator nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="vs-2017"

Ten kreator umożliwia dodawanie klasy MFC z biblioteki typów dostępne. Kreator utworzy klasę dla każdego interfejsu, który dodasz z wybranej biblioteki typów.

- **Dodaj klasę**

   Określa lokalizację biblioteki typów, z którego jest tworzony klasy.

   |Opcja|Opis|
   |------------|-----------------|
   |**Registry**|Biblioteka typów jest zarejestrowany w systemie. Zarejestrowanego typu biblioteki są wymienione w **bibliotek typów dostępnych**.|
   |**Plik**|Biblioteka typów nie zawsze jest zarejestrowany w systemie, ale jest zawarty w pliku. Należy podać lokalizację pliku w **lokalizacji**.|

- **Biblioteki typów dostępne**

   Wyświetla listę bibliotek typów w danym momencie zarejestrowany w systemie. Wybierz bibliotekę typów z tej listy, aby wyświetlić swoje interfejsy w **interfejsów** listy.

   Zobacz "wewnątrz rozproszonego modelu COM: Wpisz biblioteki oraz integracji języków"w bibliotece MSDN, aby uzyskać więcej informacji na temat rejestrowania biblioteki typów.

- **Lokalizacja**

   Określa lokalizację biblioteki typów. Jeśli klikniesz **pliku** w obszarze **dodawania klasy z**, możesz określić lokalizację pliku zawierającego bibliotekę typów. Aby przejść do lokalizacji pliku, kliknij przycisk oznaczony wielokropkiem.

- **Interfejsy**

   Wyświetla listę interfejsów w aktualnie wybranego w bibliotece typów **bibliotek typów dostępnych** listy.

   |Przycisk transferu|Opis|
   |---------------------|-----------------|
   |**>**|Dodaje interfejs aktualnie wybrany w **interfejsów** listy. Nieaktywne, jeśli interfejs nie jest zaznaczone.|
   |**>>**|Dodaje wszystkie interfejsy w bibliotece typów aktualnie wybrany w **bibliotek typów dostępnych** listy.|
   |**\<**|Usuwa klasę aktualnie wybrany w **wygenerowane klasy** listy. Wygaszony, jeśli klasa nie jest aktualnie wybrany w **wygenerowane klasy** listy.|
   |**\<\<**|Usuwa wszystkie klasy w **wygenerowane klasy** listy. Jeśli wygaszone **wygenerowane klasy** lista jest pusta.|

- **Wygenerowane klasy**

   Określa nazwy klas, które było generowane przy użyciu interfejsów, dodać za pomocą **>** lub **>>** przycisku. Kliknięcie tego pola Wybierz klasę, a następnie górę lub w dół klucze, aby przewijać listę, wyświetlając nazwę każdej klasy w **klasy** okno i nazwę pliku w **pliku** pole, Kreator generuje, kiedy można Kliknij przycisk **Zakończ**. Jednocześnie można wybrać tylko jedną klasę, w tym polu.

   Klasę można usunąć, wybierając ją na tej liście i klikając **<**. Nie musisz wybrać klasę w polu wygenerowanej klasy, aby usunąć wszystkie klasy; klikając **<<**, Usuń wszystkie klasy w **wygenerowane klasy** pole.

- **Class**

   Określa nazwę klasy, wybranego w **wygenerowane klasy** pole, które Kreator dodaje po kliknięciu **Zakończ**. Można edytować nazwy w **klasy** pole.

- **Plik**

   Określa nazwę pliku nagłówka dla nowej klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **wygenerowane klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Klasa MFC z biblioteki typów](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)<br/>
[Klienci automatyzacji: korzystanie z bibliotek typów](../../mfc/automation-clients-using-type-libraries.md)
