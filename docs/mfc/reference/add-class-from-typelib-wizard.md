---
title: Kreator dodawania klasy z biblioteki typów
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.typelib
helpviewer_keywords:
- Add Class from TypeLib Wizard [MFC]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
ms.openlocfilehash: a2c291e1c9e78d288bdb2d15f224520d764dfa1b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273884"
---
# <a name="add-class-from-typelib-wizard"></a>Kreator dodawania klasy z biblioteki typów

Ten kreator umożliwia dodawanie klasy MFC z biblioteki typów dostępne. Kreator utworzy klasę dla każdego interfejsu, który dodasz z wybranej biblioteki typów.

> [!WARNING]
> W programie Visual Studio 2017 w wersji 15.9 tego kreatora kodu jest przestarzały i zostanie usunięta w przyszłych wersjach programu Visual Studio. Ten kreator jest rzadko używana. Ogólna obsługa biblioteki ATL i MFC nie ulega zmianie poprzez usunięcie tego kreatora. Jeśli chcesz przekazać opinię dotyczącą tego wycofywania, wypełnij [w ramach tej ankiety](https://www.surveymonkey.com/r/QDWKKCN). Twoja opinia ma znaczenie dla nas.

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

## <a name="see-also"></a>Zobacz także

[Klasa MFC z biblioteki typów](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)<br/>
[Klienci automatyzacji: Korzystanie z bibliotek typów](../../mfc/automation-clients-using-type-libraries.md)
