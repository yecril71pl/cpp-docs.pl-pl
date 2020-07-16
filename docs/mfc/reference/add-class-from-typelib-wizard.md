---
title: Kreator dodawania klasy z biblioteki typów
ms.date: 05/09/2019
helpviewer_keywords:
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
ms.openlocfilehash: 6fa1dd3985fd5b565bcc4b4727f41960d1f4f5d0
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405133"
---
# <a name="add-class-from-typelib-wizard"></a>Kreator dodawania klasy z biblioteki typów

::: moniker range="vs-2019"

Ten Kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Użyj tego kreatora, aby dodać klasę MFC z dostępnej biblioteki typów. Kreator tworzy klasę dla każdego interfejsu dodawanego z wybranej biblioteki typów.

- **Dodaj klasę z**

   Określa lokalizację biblioteki typów, z której zostanie utworzona klasa.

   |Opcja|Opis|
   |------------|-----------------|
   |**Rejestr**|Biblioteka typów jest zarejestrowana w systemie. Zarejestrowane biblioteki typów są wymienione w **dostępnych bibliotekach typów**.|
   |**Plik**|Biblioteka typów nie musi być zarejestrowana w systemie, ale jest zawarta w pliku. Należy podać lokalizację pliku w **lokalizacji**.|

- **Dostępne biblioteki typów**

   Wyświetla listę bibliotek typów aktualnie zarejestrowanych w systemie. Wybierz bibliotekę typów z tej listy, aby wyświetlić jej interfejsy na liście **interfejsy** .

- **Lokalizacja**

   Określa lokalizację biblioteki typów. Jeśli klikniesz pozycję **plik** w obszarze **Dodaj klasę z**, możesz podać lokalizację pliku zawierającego bibliotekę typów. Aby przejść do lokalizacji pliku, kliknij przycisk wielokropka.

- **Interfejsy**

   Wyświetla listę interfejsów w bibliotece typów aktualnie wybranych na liście **dostępne biblioteki typów** .

   |Przycisk transferu|Opis|
   |---------------------|-----------------|
   |**>**|Dodaje interfejs aktualnie wybrany na liście **interfejsy** . Wygaszone, jeśli nie wybrano interfejsu.|
   |**>>**|Dodaje wszystkie interfejsy w bibliotece typów aktualnie zaznaczonej na liście **dostępne biblioteki typów** .|
   |**\<**|Usuwa klasę aktualnie wybraną z listy **wygenerowanych klas** . Wygaszone, jeśli żadna Klasa nie jest obecnie zaznaczona na liście **wygenerowanych klas** .|
   |**\<\<**|Usuwa wszystkie klasy z listy **wygenerowanych klas** . Wygaszone, jeśli lista **wygenerowanych klas** jest pusta.|

- **Wygenerowane klasy**

   Określa nazwy klas do wygenerowania z interfejsów dodanych za pomocą **>** przycisku lub **>>** . Możesz kliknąć to pole, aby wybrać klasę, a następnie użyć klawiszy w górę lub w dół, aby przewijać listę, wyświetlając każdą nazwę klasy w polu **Klasa** i nazwę pliku w polu **plik** generowanym przez kreatora po kliknięciu przycisku **Zakończ**. W tym polu można wybrać tylko jedną klasę naraz.

   Możesz usunąć klasę, wybierając ją na tej liście i klikając **<** . Nie trzeba wybierać klasy w polu wygenerowane klasy, aby usunąć wszystkie klasy; klikając **<<** , należy usunąć wszystkie klasy w polu **wygenerowane klasy** .

- **Klasa**

   Określa nazwę klasy wybranej w polu **wygenerowane klasy** , którą Kreator dodaje po kliknięciu przycisku **Zakończ**. Nazwę można edytować w polu Class ( **Klasa** ).

- **Plik**

   Ustawia nazwę pliku nagłówka dla nowej klasy. Domyślnie ta nazwa jest oparta na nazwie dostarczanej w **wygenerowanych klasach**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji, lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji, dopóki nie klikniesz przycisku **Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Klasa MFC z biblioteki typów](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)<br/>
[Klienci automatyzacji: korzystanie z bibliotek typów](../../mfc/automation-clients-using-type-libraries.md)
