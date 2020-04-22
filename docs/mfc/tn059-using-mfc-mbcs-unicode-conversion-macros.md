---
title: 'TN059: używanie makr konwersji MFC MBCS-Unicode'
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
ms.openlocfilehash: 657381d8247aef14b2c725996dfeb11d0e0535fe
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749442"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: używanie makr konwersji MFC MBCS/Unicode

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano sposób używania makr do konwersji MBCS/Unicode, które są zdefiniowane w afxpriv. H. Te makra są najbardziej przydatne, jeśli aplikacja zajmuje się bezpośrednio z OLE API lub z jakiegoś powodu, często musi konwertować między Unicode i MBCS.

## <a name="overview"></a>Omówienie

W MFC 3.x użyto specjalnej biblioteki DLL (MFCANS32. DLL), aby automatycznie konwertować między Unicode i MBCS, gdy interfejsy OLE zostały wywołane. Ta biblioteka DLL była warstwą prawie przezroczystą, która umożliwiała zapis aplikacji OLE tak, jakby interfejsy i interfejsy OLE były MBCS, mimo że zawsze są unicode (z wyjątkiem komputerów Macintosh). Chociaż ta warstwa była wygodna i pozwalała na szybkie przenoszenie aplikacji z Win16 do Win32 (MFC, Microsoft Word, Microsoft Excel i VBA, to tylko niektóre z aplikacji firmy Microsoft, które korzystały z tej technologii), miała czasami znaczący hit wydajności. Z tego powodu MFC 4.x nie używa tej biblioteki DLL i zamiast tego prowadzi rozmowy bezpośrednio do interfejsów Ole Unicode. Aby to zrobić, MFC musi przekonwertować na Unicode do MBCS podczas wywoływania interfejsu OLE i często musi konwertować na MBCS z Unicode podczas implementowania interfejsu OLE. Aby poradzić sobie z tym wydajnie i łatwo, stworzono szereg makr, aby ułatwić tę konwersję.

Jedną z największych przeszkód tworzenia takiego zestawu makr jest alokacja pamięci. Ponieważ ciągi nie mogą być konwertowane w miejscu, nowa pamięć do przechowywania przekonwertowanych wyników muszą być przydzielone. Można to zrobić za pomocą kodu podobnego do następującego:

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

Takie podejście jako szereg problemów. Głównym problemem jest to, że jest dużo kodu do pisania, testowania i debugowania. Coś, co było prostym wywołaniem funkcji, jest teraz o wiele bardziej złożone. Ponadto istnieje znaczne obciążenie środowiska uruchomieniowego w ten sposób. Pamięć musi być przydzielona na stercie i zwolniona za każdym razem, gdy konwersja jest wykonywana. Na koniec powyższy kod musiałby `#ifdefs` mieć odpowiednie dodane dla unicode i Macintosh kompilacji (które nie wymagają tej konwersji miało miejsce).

Rozwiązanie, które wymyśliliśmy, polega na utworzeniu niektórych makr, które 1) maskują różnicę między różnymi platformami, a 2) używają efektywnego schematu alokacji pamięci, a 3) są łatwe do wstawienia do istniejącego kodu źródłowego. Oto przykład jednej z definicji:

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

Korzystanie z tego makra zamiast kodu powyżej i rzeczy są znacznie prostsze:

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Istnieją dodatkowe połączenia, w których konwersja jest konieczna, ale korzystanie z makr jest proste i skuteczne.

Implementacja każdego makra używa funkcji _alloca() do przydzielania pamięci ze stosu zamiast sterty. Przydzielanie pamięci ze stosu jest znacznie szybsze niż przydzielanie pamięci na stercie, a pamięć jest automatycznie zwalniana po zakończeniu funkcji. Ponadto makra unikają `MultiByteToWideChar` wywoływania `WideCharToMultiByte`(lub) więcej niż jeden raz. Odbywa się to poprzez przydzielenie nieco więcej pamięci niż jest to konieczne. Wiemy, że MBC przekonwertuje się na co najwyżej jeden **WCHAR** i że dla każdego **WCHAR** będziemy mieli maksymalnie dwa bajty MBC. Przydzielając trochę więcej niż to konieczne, ale zawsze wystarczy do obsługi konwersji drugie wywołanie drugie wywołanie funkcji konwersji jest unikać. Wywołanie funkcji `AfxA2Whelper` pomocnika zmniejsza liczbę wypycheń argumentów, które należy wykonać w celu wykonania konwersji (powoduje to mniejszy kod, niż jeśli jest wywoływana `MultiByteToWideChar` bezpośrednio).

Aby makra miały miejsce do przechowywania tymczasowej długości, konieczne jest zadeklarowanie zmiennej lokalnej o nazwie _convert która robi to w każdej funkcji korzystającej z makr konwersji. Odbywa się to poprzez wywołanie makra USES_CONVERSION, jak pokazano powyżej w przykładzie.

Istnieją zarówno ogólne makra konwersji, jak i makra specyficzne dla OLE. Te dwa różne zestawy makr zostały omówione poniżej. Wszystkie makra znajdują się w AFXPRIV. H.

## <a name="generic-conversion-macros"></a>Ogólne makra konwersji

Ogólne makra konwersji tworzą podstawowy mechanizm. Przykład makra i implementacja pokazana w poprzedniej sekcji, A2W, jest jednym z takich "ogólnych" makr. Nie jest to związane z OLE specjalnie. Zestaw makr rodzajowych jest wymieniony poniżej:

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

Oprócz konwersji tekstu, istnieją również makra i funkcje `DEVMODE` `BSTR`pomocnicze do konwersji `TEXTMETRIC`, , i OLE przydzielone ciągi. Te makra są poza zakresem tej dyskusji - patrz AFXPRIV. H, aby uzyskać więcej informacji na temat tych makr.

## <a name="ole-conversion-macros"></a>Makra konwersji OLE

Makra konwersji OLE są przeznaczone specjalnie do obsługi funkcji, które oczekują znaków **OLESTR.** Jeśli zbadasz nagłówki OLE, zobaczysz wiele odwołań do **LPCOLESTR** i **OLECHAR**. Te typy są używane do odwoływania się do typu znaków używanych w interfejsach OLE w sposób, który nie jest specyficzny dla platformy. **OLECHAR** mapuje **na char** na platformach Win16 i Macintosh oraz **WCHAR** w win32.

Aby utrzymać liczbę **#ifdef** dyrektyw w kodzie MFC do minimum mamy podobne makro dla każdej konwersji, w którym są zaangażowane ciągi OLE. Najczęściej używane są następujące makra:

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Ponownie istnieją podobne makra do wykonywania textmetric, DEVMODE, BSTR i OLE przydzielone ciągi. Patrz AFXPRIV. H, aby uzyskać więcej informacji.

## <a name="other-considerations"></a>Inne zagadnienia

Nie używaj makr w ciasnej pętli. Na przykład nie chcesz pisać następującego rodzaju kodu:

```cpp
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

Powyższy kod może spowodować przydzielanie megabajtów pamięci na stosie `lpsz` w zależności od zawartości ciągu! Konwersja ciągu dla każdej iteracji pętli wymaga również czasu. Zamiast tego przenieś takie stałe konwersje z pętli:

```cpp
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Jeśli ciąg nie jest stała, następnie hermetyzować wywołanie metody do funkcji. Umożliwi to zwalnianie buforu konwersji za każdym razem. Przykład:

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

Nigdy nie zwracaj wyniku jednego z makr, chyba że wartość zwracana oznacza wykonanie kopii danych przed zwróceniem. Na przykład ten kod jest zły:

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

Powyższy kod można naprawić, zmieniając wartość zwracaną na coś, co kopiuje wartość:

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

Makra są łatwe w użyciu i łatwe do wstawienia do kodu, ale jak można powiedzieć z powyższych zastrzeżeń, musisz być ostrożny podczas ich używania.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
