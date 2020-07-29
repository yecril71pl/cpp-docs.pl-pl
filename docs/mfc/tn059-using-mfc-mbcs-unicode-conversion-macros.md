---
title: 'TN059: korzystanie z makr konwersji MFC MBCS-Unicode'
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: d689e87b8f2804fe99804c6ca37a48bac01df263
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182736"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: używanie makr konwersji MFC MBCS/Unicode

> [!NOTE]
> Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

W tej uwadze opisano, jak używać makr dla konwersji MBCS/Unicode, które są zdefiniowane w AFXPRIV. C. Te makra są najbardziej przydatne, jeśli aplikacja zajmuje się bezpośrednio z interfejsem API OLE lub z jakiegoś powodu, często wymaga konwersji między Unicode i MBCS.

## <a name="overview"></a>Omówienie

W MFC 3. x specjalna Biblioteka DLL została użyta (MFCANS32.DLL) do automatycznego konwersji między Unicode i MBCS po wywołaniu interfejsów OLE. Ta biblioteka DLL była prawie przezroczystą warstwą, która umożliwia zapisywanie aplikacji OLE, tak jakby interfejsy API OLE i interfejsy były MBCS, nawet jeśli są zawsze w formacie Unicode (z wyjątkiem komputerów Macintosh). Chociaż ta warstwa była wygodna i dozwolone aplikacje są szybko przechodzące z Win16 do Win32 (MFC, Microsoft Word, Microsoft Excel i VBA), to tylko niektóre aplikacje firmy Microsoft korzystające z tej technologii), w przypadku których nastąpiło nieznacznie duże wykorzystanie wydajności. Z tego powodu MFC 4. x nie używa tej biblioteki DLL i zamiast tego nadaje się bezpośrednio do interfejsów Unicode OLE. Aby to zrobić, MFC musi przekonwertować do formatu Unicode na MBCS podczas wykonywania wywołania interfejsu OLE i często musi skonwertować do MBCS z Unicode podczas implementowania interfejsu OLE. Aby ułatwić szybkie i łatwe obsługiwanie, utworzono kilka makr w celu ułatwienia tej konwersji.

Jednym z największych progów tworzenia takiego zestawu makr jest alokacja pamięci. Ponieważ ciągów nie można przekonwertować na miejsce, należy przydzielić nową pamięć do przechowywania przekonwertowanych wyników. Można to zrobić przy użyciu kodu podobnego do poniższego:

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

Takie podejście jako wiele problemów. Główny problem polega na tym, że jest to dużo kodu do zapisu, testowania i debugowania. Coś, który był prostym wywołaniem funkcji, jest teraz znacznie bardziej skomplikowany. Ponadto istnieje znaczny nakład pracy w czasie wykonywania. Pamięć musi być przydzielana na stercie i zwalniana przy każdej konwersji. Na koniec należy dodać odpowiedni kod `#ifdefs` dla kompilacji Unicode i Macintosh (nie wymaga to konwersji).

Rozwiązanie, które zostało dołączone do programu, to utworzenie niektórych makr, które 1) maskuje różnice między różnymi platformami, a 2) wykorzystują wydajny schemat alokacji pamięci, a 3) można łatwo wstawić do istniejącego kodu źródłowego. Oto przykład jednej z definicji:

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

Użycie tego makra zamiast kodu powyżej i jest znacznie prostsze:

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Istnieją dodatkowe wywołania, w których konwersja jest konieczna, ale korzystanie z makr jest proste i skuteczne.

Implementacja każdego makra używa funkcji _alloca () w celu przydzielenia pamięci ze stosu zamiast sterty. Przydzielanie pamięci ze stosu jest znacznie szybsze niż przydzielanie pamięci na stercie, a pamięć jest zwalniana automatycznie po zamknięciu funkcji. Ponadto makra unikają wywoływania `MultiByteToWideChar` (lub `WideCharToMultiByte` ) więcej niż jeden raz. Jest to realizowane przez przydzielenie nieco większej ilości pamięci niż jest to konieczne. Wiemy, że MBC zostanie przekonwertowane na co najmniej jeden **WCHAR** i że dla każdego **WCHAR** będziemy mieć co najwyżej dwa MBC bajtów. Przydzielając nieco więcej niż to konieczne, ale zawsze wystarczą, aby obsłużyć konwersję, należy uniknąć drugiego wywołania funkcji konwersji. Wywołanie funkcji pomocnika `AfxA2Whelper` zmniejsza liczbę operacji wypychania argumentu, które muszą zostać wykonane, aby można było wykonać konwersję (wynikiem jest mniejszy kod, jeśli jest on wywoływany `MultiByteToWideChar` bezpośrednio).

Aby makra miały miejsce do przechowywania tymczasowej długości, należy zadeklarować zmienną lokalną o nazwie _convert, która robi to w każdej funkcji, która używa makr konwersji. W tym celu należy wycofać makro USES_CONVERSION jak pokazano powyżej w przykładzie.

Istnieją zarówno ogólne makra konwersji, jak i makra specyficzne dla OLE. Te dwa różne zestawy makr zostały omówione poniżej. Wszystkie makra znajdują się w AFXPRIV. C.

## <a name="generic-conversion-macros"></a>Makra konwersji ogólnej

Makra konwersji ogólnej tworzą podstawowy mechanizm. Przykładem makra i implementacją przedstawioną w poprzedniej sekcji A2W, jest jednym z takich "ogólnych" makr. Nie jest on powiązany z mechanizmem OLE specyficznym dla programu. Poniżej znajduje się zestaw ogólnych makr:

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

Oprócz konwersji tekstu, istnieją także makra i funkcje pomocnika do konwertowania `TEXTMETRIC` ciągów, `DEVMODE` , `BSTR` i. Te makra wykraczają poza zakres tej dyskusji — zapoznaj się z AFXPRIV. H Aby uzyskać więcej informacji na temat tych makr.

## <a name="ole-conversion-macros"></a>Makra konwersji OLE

Makra konwersji OLE zostały zaprojektowane specjalnie w celu obsługi funkcji, które oczekują **OLESTR** znaków. Jeśli przebadasz nagłówki OLE, zobaczysz wiele odwołań do **LPCOLESTR** i **OLECHAR**. Te typy są używane do odwoływania się do typu znaków używanych w interfejsach OLE w sposób, który nie jest specyficzny dla danej platformy. **OLECHAR** Maps na **`char`** platformie Win16 i komputerów Macintosh i **WCHAR** w systemie Win32.

Aby zachować liczbę dyrektyw **#ifdef** w kodzie MFC do minimum, mamy podobne makro dla każdej konwersji, w której występują ciągi OLE. Następujące makra są najczęściej używane:

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Ponownie istnieją podobne makra do wykonywania ciągów znaków TEXTMETRIC, DEVMODE, BSTR i OLE. Zapoznaj się z AFXPRIV. H Aby uzyskać więcej informacji.

## <a name="other-considerations"></a>Inne zagadnienia

Nie używaj makr w ścisłej pętli. Na przykład nie chcesz pisać następującego rodzaju kodu:

```cpp
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

Powyższy kod może spowodować przydzielenie megabajtów pamięci na stosie w zależności od zawartości ciągu `lpsz` ! Konwersja ciągu dla każdej iteracji pętli wymaga również czasu. Zamiast tego Przenieś takie stałe konwersje z pętli:

```cpp
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Jeśli ciąg nie jest stałą, należy hermetyzować wywołanie metody do funkcji. Pozwoli to zwolnić bufor konwersji za każdym razem. Na przykład:

```cpp
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

Nigdy nie zwracaj wyniku jednego z makr, chyba że zwracana wartość oznacza utworzenie kopii danych przed zwróceniem. Na przykład ten kod jest nieodpowiedni:

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

Powyższy kod można naprawić, zmieniając wartość zwracaną na element, który kopiuje wartość:

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

Makra są łatwe w użyciu i można je łatwo wstawiać do kodu, ale w celu poinformowania o powyższych zastrzeżeniach należy zachować ostrożność przy ich użyciu.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numeru](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
