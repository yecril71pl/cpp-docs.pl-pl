---
title: 'TN059: Używanie makr konwersji MBCS-Unicode w MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.mbcs
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
ms.openlocfilehash: 130b459dc87f36325d0f253181a196bea868856f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399619"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: Przy użyciu makr konwersji MFC MBCS/Unicode

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje sposób używania makra konwersji MBCS/Unicode są zdefiniowane w AFXPRIV. H. Te makra są najbardziej przydatne, jeśli swoimi ofertami aplikacji bezpośrednio za pomocą interfejsu API OLE lub jakiegoś powodu często wymaga konwersji między Unicode i MBCS.

## <a name="overview"></a>Omówienie

W MFC 3.x, specjalne DLL został używane (MFCANS32. Biblioteka DLL) aby dokonać automatycznej konwersji między Unicode i MBCS wywołanego interfejsy OLE. Ta biblioteka DLL była prawie przezroczyste warstwy, które dozwolone aplikacje OLE do zapisania jak gdyby interfejsów i interfejsów API OLE MBCS, nawet jeśli są one zawsze Unicode (z wyjątkiem komputerów Macintosh). Podczas tej warstwie jest wygodne i dozwolone aplikacje mogą być szybko przenoszone z Win16 do Win32 (MFC, program Microsoft Word, program Microsoft Excel i VBA, są tylko niektóre aplikacje firmy Microsoft, używane tej technologii), jakby posiadała czasami istotnie poprawiającą wydajność trafień. Z tego powodu MFC 4.x nie korzysta z tej biblioteki DLL i zamiast tego komunikuje się bezpośrednio z interfejsy Unicode OLE. Aby to zrobić, trzeba przekonwertować do formatu Unicode do MBCS, podczas nawiązywania połączenia z interfejsem OLE MFC, a często wymaga konwertować do MBCS ze standardu Unicode podczas implementowania interfejsu OLE. Aby umożliwić obsługę, wydajnego i łatwego, wielu makr zostały utworzone, aby ułatwić tę konwersję.

Jedną z największych przeszkód tworzenia zestawu makra jest alokacji pamięci. Ponieważ nie można przekonwertować ciągi w miejscu, muszą być przydzielane nowej pamięci do przechowywania wyników przekonwertowana. To może zostały wykonane przy użyciu kodu podobne do następujących:

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

To podejście jako liczba problemów. Głównym problemem jest duża ilość kodu do zapisu, testowania i debugowania. Coś, co zostało wywołanie prostej funkcji jest teraz znacznie bardziej złożone. Ponadto istnieje runtime znaczne obciążenie w ten sposób. Pamięci musi być przydzielony na stosie i zwolniona z każdym razem, gdy jest wykonywane w konwersji. Na koniec powyższy kod muszą znaleźć się odpowiednie `#ifdefs` dodano dla kompilacji dla komputerów Macintosh i Unicode, (które nie wymagają tej konwersji).

Rozwiązanie nad którym zdecydowaliśmy się za pomocą jest tworzenie niektóre makra, w których (1) maski różnica między różnymi platformami i (2) Użyj schematu alokacji pamięci wydajne i (3) są łatwe do wstawienia do istniejącego kodu źródłowego. Oto przykład jednej z definicji:

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

Przy użyciu tego makra zamiast powyższy kod i elementy są dużo prostsze:

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Istnieją dodatkowe wywołania, gdy konwersja jest niezbędne, ale przy użyciu makra jest prosta i skuteczna.

Implementacja każdego makra funkcja _alloca() została można przydzielić pamięci ze stosu, zamiast stosu. Alokacja pamięci ze stosu jest znacznie wyższa niż przydzielania pamięci na stosie, a pamięć jest zwalniana automatycznie, gdy funkcja jest został zakończony. Ponadto, makra unikać wywoływania `MultiByteToWideChar` (lub `WideCharToMultiByte`) więcej niż jeden raz. Odbywa się to poprzez przydzielanie trochę więcej pamięci niż jest to konieczne. Wiemy, że MBC zostanie przekonwertowana na co najwyżej jeden **WCHAR** oraz że dla każdego **WCHAR** firma Microsoft będzie mieć co najwyżej dwa bajty MBC. Przydzielając nieco więcej niż jest to konieczne, ale zawsze wystarczająco do obsługi konwersji, drugie wywołanie drugie wywołanie funkcji konwersji jest unikane. Wywołanie funkcji pomocnika `AfxA2Whelper` zmniejsza liczbę wypchnięć argumentów, które muszą być wykonane w celu wykonania konwersji (powoduje to mniejszego kodu niż Jeśli wywoływana `MultiByteToWideChar` bezpośrednio).

W celu makr, które mają miejsce do przechowywania tymczasowych długości, należy zadeklarować zmiennej lokalnej o nazwie _konwertuj tak, to w każdej funkcji, która korzysta z makr konwersji. Odbywa się to przez wywołanie makra USES_CONVERSION, jak pokazano w przykładzie powyżej.

Istnieją zarówno makra konwersji ogólny, jak i makra określonych OLE. Te dwa zestawy inne makro omówiono poniżej. Wszystkie makra znajdują się w AFXPRIV. H.

## <a name="generic-conversion-macros"></a>Makra konwersji ogólny

Makra konwersji ogólny formularz podstawowy mechanizm. Przykład — makro i implementacji pokazano w poprzedniej sekcji, A2W, jest jedno takie makro "generic". Nie jest powiązany do OLE specjalnie. Zestaw ogólnych makr znajduje się poniżej:

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

Oprócz wykonywania konwersji tekstu, dostępne są także makra i funkcje pomocnicze do konwertowania `TEXTMETRIC`, `DEVMODE`, `BSTR`i OLE przydzielone ciągów. Te makra wykraczają poza zakres tej dyskusji — dotyczą AFXPRIV. Godz. Aby uzyskać więcej informacji na temat tych makr.

## <a name="ole-conversion-macros"></a>Makra konwersji OLE

Makra konwersji OLE są przeznaczone specjalnie do obsługi funkcji, które oczekują **OLESTR** znaków. Jeśli możesz sprawdzić nagłówki OLE, pojawią się wiele odwołań do **LPCOLESTR** i **OLECHAR**. Te typy są używane do odwoływania się do typu znaków w interfejsy OLE w sposób, który nie jest specyficzne dla platformy. **OLECHAR** mapuje **char** na platformach Win16 oraz dla komputerów Macintosh i **WCHAR** w systemie Win32.

Aby zachować liczbę **#ifdef** dyrektywy w MFC kodu do minimum mamy podobne makra dla każdego konwersji, gdzie ciągi OLE są zaangażowane. Następujące makra są najczęściej stosowane:

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Ponownie są podobne makra do wykonywania TEXTMETRIC, DEVMODE, BSTR i OLE przydzielone ciągów. Zapoznaj się z AFXPRIV. Godz. Aby uzyskać więcej informacji.

## <a name="other-considerations"></a>Inne zagadnienia

Nie należy używać makr w pętli. Na przykład czy chcesz zapisać następujące rodzaj kodu:

```
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

Powyższy kod może spowodować przydzielanie megabajty pamięci na stosie, w zależności od tego, jakie zawartość ciągu `lpsz` jest! Ponadto czas można przekonwertować ciągu dla każdej iteracji pętli. Zamiast tego Przenieś takie konwersje stałe dostęp do najaktualniejszych:

```
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Jeśli ciąg nie jest stałą, następnie hermetyzować wywołanie metody do funkcji. Umożliwi to buforu konwersji ma zostać zwolniony każdorazowo. Na przykład:

```
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

Nigdy nie należy zwracać wynik makra, chyba że zwracana wartość wskazuje, skopiowanie danych przed powrotu. Na przykład ten kod jest nieprawidłowy:

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

Powyższy kod może zostać naprawione, zmieniając wartość zwracaną coś, co powoduje skopiowanie wartości:

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

Makra są łatwe w użyciu i łatwe do wstawienia w kodzie, ale jak można stwierdzić, że z powyższych ostrzeżenia, należy uważać podczas korzystania z nich.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
