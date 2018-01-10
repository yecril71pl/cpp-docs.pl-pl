---
title: "TN059: Używanie makr konwersji MFC MBCS na Unicode | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.mbcs
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 45df45fe3d06e71b33c20ecd88d3f958a5673df1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: używanie makr konwersji MFC MBCS/Unicode
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga informacje dotyczące używania makra konwersji MBCS/Unicode, które są zdefiniowane w AFXPRIV. H. Następujące makra są najbardziej przydatne, jeśli w Twojej oferty aplikacji bezpośrednio z OLE API lub jakiegoś powodu często wymaga konwersji między Unicode i MBCS.  
  
## <a name="overview"></a>Omówienie  
 W MFC 3.x specjalne DLL został użyty (MFCANS32. Biblioteki DLL) aby dokonać automatycznej konwersji między Unicode i MBCS wywołanego interfejsy OLE. Ta biblioteka DLL została prawie przezroczyste warstwy, która może aplikacje OLE ma zostać zapisany tak, jakby OLE interfejsów API i interfejsów był MBCS, nawet jeśli są one zawsze Unicode (z wyjątkiem komputerów Macintosh). Ta warstwa to wygodny i dozwolone aplikacje mogą szybko być przenoszone do systemu Win32 Win16 (MFC, program Microsoft Word, Microsoft Excel i VBA, są tylko niektóre z aplikacji firmy Microsoft, które używane tej technologii), miał czasami znaczących wydajności trafień. Z tego powodu MFC 4.x nie korzysta z tej biblioteki DLL i zamiast tego komunikuje się bezpośrednio do interfejsy Unicode OLE. Aby to zrobić, MFC musi zostać przekonwertowany na Unicode do MBCS podczas nawiązywania połączenia z interfejsem OLE i często wymaga konwertować do MBCS z Unicode podczas implementowania interfejsu OLE. Aby umożliwić obsługę, wydajne i łatwe, liczba makra zostały utworzone ułatwiają konwersji.  
  
 Jedną z największych przeszkód tworzenia zestaw makra jest alokacji pamięci. Ponieważ nie można przekonwertować ciągi w miejscu, należy można przydzielić nowej pamięci do przechowywania wyników przekonwertowany. To może zostały wykonane z kodem podobny do następującego:  
  
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
  
 Takie podejście jako szereg problemów. Główny problem, jest dużo kodu do zapisu, testowania i debugowania. Coś, co zostało wywołanie funkcji prostego jest teraz bardziej złożonych. Ponadto istnieje znaczne środowiska uruchomieniowego obciążenie w ten sposób. Pamięci musi zostać przydzielone na stercie zwolnienia i uwolnienia zawsze, gdy jest wykonywane konwersji. Na koniec powyższy kod musi dysponować odpowiednie `#ifdefs` dodano w programie Unicode i Macintosh kompilacji (które nie wymagają tej konwersji).  
  
 Rozwiązanie, które zdecydowaliśmy się z jest tworzenie niektóre makra, które 1) maski różnica między różnymi platformami i 2) Użyj schematu alokacji pamięci wydajne i 3) są łatwe do wstawienia do istniejącego kodu źródłowego. Oto przykład jednej definicji:  
  
```  
#define A2W(lpa) (\  
 ((LPCSTR)lpa == NULL) NULL : (\  
    _convert = (strnlen(lpa)+1),\  
    AfxA2WHelper((LPWSTR) alloca(_convert*2),   
    lpa,
    _convert)\)\)  
```  
  
 Przy użyciu tego makra zamiast kodu powyżej i rzeczy jest znacznie prostsze:  
  
```  
// use it to call OLE here  
USES_CONVERSION;  
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```  
  
 Istnieją dodatkowe wywołania, gdy konwersja jest konieczne, ale przy użyciu makra jest prosta i skuteczna.  
  
 Implementacja każdego makra funkcja _alloca() została można przydzielić pamięci ze stosu zamiast sterty. Przydzielanie pamięci ze stosu jest znacznie szybsza niż przydzielania pamięci na stosie, a pamięć zwalnia się automatycznie, gdy funkcja jest zakończony. Ponadto makra Unikaj wywoływania **MultiByteToWideChar** (lub **Procedura WideCharToMultiByte**) więcej niż jeden raz. Jest to realizowane przez przydzielanie nieco więcej pamięci niż jest to konieczne. Wiemy, że MBC przekonwertuje do co najwyżej jeden **WCHAR** oraz że dla każdego **WCHAR** firma Microsoft będzie mieć co najwyżej dwa bajty MBC. Przydzielając nieco więcej niż jest to konieczne, ale zawsze wystarczająco do obsługi konwersji, drugie wywołanie drugi unika się wywołanie funkcji konwersji. Wywołanie funkcji pomocnika **AfxA2Whelper** zmniejsza liczbę wypchnięć argumentu, które należy wykonać w celu wykonania konwersji (powoduje to kodu mniejsze niż Jeśli mu **MultiByteToWideChar**bezpośrednio).  
  
 W celu makr mieć miejsca do przechowywania tymczasowych długości, należy zadeklarować zmiennej lokalnej o nazwie _konwertuj, który dokonuje tego w każdej funkcji który korzysta z makra konwersji. Jest to realizowane przez wywoływanie **USES_CONVERSION** makra, jak pokazano w przykładzie powyżej.  
  
 Istnieją zarówno makra konwersji ogólny, jak i makra określonych OLE. Poniżej omówiono te dwa zestawy różnych — makro Wszystkie makra znajdują się w AFXPRIV. H.  
  
## <a name="generic-conversion-macros"></a>Makra konwersji ogólny  
 Makra konwersji ogólnego tworzą podstawowy mechanizm. Przykład makro i wyświetlone w poprzedniej sekcji, A2W, implementacja jest jedno takie makro "Ogólne". Nie jest powiązana do OLE w szczególności. Zbiór ogólne makra jest wyświetlony poniżej:  
  
```  
A2CW      (LPCSTR) -> (LPCWSTR)  
A2W      (LPCSTR) -> (LPWSTR)  
W2CA      (LPCWSTR) -> (LPCSTR)  
W2A      (LPCWSTR) -> (LPSTR)  
```  
  
 Oprócz wykonywania konwersji tekstu, dostępne są także makra i funkcje pomocnicze do konwertowania `TEXTMETRIC`, `DEVMODE`, `BSTR`i OLE przydzielone ciągów. Te makra wykraczają poza zakres tej dyskusji — dotyczą AFXPRIV. H, aby uzyskać więcej informacji na temat tych makr.  
  
## <a name="ole-conversion-macros"></a>Makra konwersji OLE  
 Makra konwersji OLE są zaprojektowane specjalnie z myślą o obsługę funkcji, które oczekują **OLESTR** znaków. Należy sprawdzić nagłówki OLE, będzie mógł przeglądać wiele odwołań do **LPCOLESTR** i **OLECHAR**. Te typy są używane do odwoływania się do typu znaków w interfejsy OLE w taki sposób, który nie jest specyficzne dla platformy. **OLECHAR** mapuje `char` na platformach Win16 i Macintosh i **WCHAR** w Win32.  
  
 Aby zapewnić liczbę **#ifdef** kod dyrektywy w MFC do minimum mamy makra podobne do każdej konwersji który którym są związane z ciągami OLE. Najczęściej używane są następujące makra:  
  
```  
T2COLE   (LPCTSTR) -> (LPCOLESTR)  
T2OLE   (LPCTSTR) -> (LPOLESTR)  
OLE2CT   (LPCOLESTR) -> (LPCTSTR)  
OLE2T   (LPCOLESTR) -> (LPCSTR)  
```  
  
 Ponownie, istnieją podobne makra może `TEXTMETRIC`, `DEVMODE`, `BSTR`i OLE przydzielone ciągów. Zapoznaj się AFXPRIV. H, aby uzyskać więcej informacji.  
  
## <a name="other-considerations"></a>Inne zagadnienia  
 Nie należy używać makra w ścisłej pętli. Na przykład czy chcesz zapisać następujący rodzaj kodu:  
  
```  
void BadIterateCode(LPCTSTR lpsz)  
{  
    USES_CONVERSION; 
    for (int ii = 0; ii <10000; ii++)  
    pI->SomeMethod(ii, T2COLE(lpsz));

}  
```  
  
 Powyższy kod może spowodować alokowanie w megabajtach ilość pamięci na stosie, w zależności od tego, jakie wartości ciągu `lpsz` jest! Również czas można przekonwertować ciągu dla każdej iteracji pętli. Zamiast tego należy przenieść takie stałej konwersje poza pętli:  
  
```  
void MuchBetterIterateCode(LPCTSTR lpsz)  
{  
    USES_CONVERSION; 
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)  
    pI->SomeMethod(ii, lpszT);

}  
```  
  
 Jeśli ciąg nie jest stały, następnie hermetyzować wywołanie metody do funkcji. Pozwoli to buforu konwersji ma zostać zwolniony zawsze. Na przykład:  
  
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
  
 Nigdy nie należy zwracać wynik makra, chyba że zwracana wartość oznacza skopiowanie danych przed powrotu. Na przykład ten kod jest nieprawidłowy:  
  
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
  
 Powyższy kod może stałej, zmieniając wartość zwracana do zasobu, który kopiuje wartość:  
  
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
  
 Makra są łatwe w użyciu i łatwe do wstawienia do kodu, ale jak stwierdzić, z powyższych ostrzeżenia, musisz należy zachować ostrożność przy ich użyciu.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

