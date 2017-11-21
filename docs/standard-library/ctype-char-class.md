---
title: "CType —&lt;char&gt; klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
dev_langs: C++
helpviewer_keywords: ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a48b64b60887e5a6ba627a3ca25b77d32c05778
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ctypeltchargt-class"></a>CType —&lt;char&gt; — klasa
Klasa jest jawnej specjalizacji szablonu klasy **ctype\<CharType**> na typ `char`, opisujący obiekt, który może służyć jako zestaw reguł ustawień regionalnych charakteryzujących różne właściwości znaku typu `char`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <>  
class ctype<char>  
: public ctype_base  
{  
public:  
    typedef char _Elem;  
    typedef _Elem char_type;  
    bool is(
    mask _Maskval,  
    _Elem _Ch) const;

 
    const _Elem* is(
    const _Elem* first,  
    const _Elem* last,  
    mask* dest) const;

 
    const _Elem* scan_is(
    mask _Maskval,  
    const _Elem* first,  
    const _Elem* last) const;

 
    const _Elem* scan_not(
    mask _Maskval,  
    const _Elem* first,  
    const _Elem* last) const;

 
    _Elem tolower(
    _Elem _Ch) const;

 
    const _Elem* tolower(
    _Elem* first,  
    const _Elem* last) const;

 
    _Elem toupper(
    _Elem _Ch) const;

 
    const _Elem* toupper(
    _Elem* first,  
    const _Elem* last) const;

 
    _Elem widen(
    char _Byte) const;

 
    const _Elem* widen(
    const char* first,  
    const char* last,  
    _Elem* dest) const;

 
    const _Elem* _Widen_s(
    const char* first,  
    const char* last,  
    _Elem* dest,  
    size_t dest_size) const;

 
    _Elem narrow(
    _Elem _Ch,  
    char _Dflt = '\0') const;

 
    const _Elem* narrow(
    const _Elem* first,  
    const _Elem* last,  
    char _Dflt,  
    char* dest) const;

 
    const _Elem* _Narrow_s(
    const _Elem* first,  
    const _Elem* last,  
    char _Dflt,  
    char* dest,  
    size_t dest_size) const;

 
    static locale::id& id;  
    explicit ctype(
    const mask* _Table = 0,  
    bool _Deletetable = false,  
    size_t _Refs = 0);

protected:  
    virtual ~ctype();
//other protected members  
};  
```  
  
## <a name="remarks"></a>Uwagi  
 Jawna specjalizacja różni się od klasy szablonu na kilka sposobów:  
  
-   Obiekt klasy ctype < `char`> przechowuje wskaźnik do pierwszego elementu obiektu tabeli Maska ctype, tablicę uchar_max — + 1 elementów typu **ctype_base::mask**. Przechowuje także obiekt logiczną, wskazującą, czy mają zostać usunięte tablicy (przy użyciu `operator delete[]`) podczas ctype\< **elementu**> obiekt zostanie zniszczony.  
  
-   Jej jedyny Konstruktor publiczny pozwala określić **kartę**, tabeli Maska ctype i **del**, logiczna obiekt, który ma wartość true, jeśli tablica ma być usunięte, gdy ctype < `char`> obiekt zostanie zniszczony. , a także parametr liczebności referencyjnej system plików refs.  
  
-   Funkcja chroniony element członkowski **tabeli** zwraca tabelę maski ctype przechowywane.  
  
-   Statyczny element członkowski obiektu **table_size** określa minimalną liczbę elementów w tabeli Maska ctype.  
  
-   Funkcja chronionych statyczny element członkowski **classic_table**(zwraca wartość tabeli Maska ctype odpowiednich ustawień regionalnych "C".  
  
-   Nie ma żadnych funkcji chronionego członka wirtualnego [do_is](../standard-library/ctype-class.md#do_is), [do_scan_is](../standard-library/ctype-class.md#do_scan_is), lub [do_scan_not](../standard-library/ctype-class.md#do_scan_not). Odpowiednie funkcje publicznego elementu członkowskiego wykonywać operacje równoważne samodzielnie.  
  
 Funkcje Członkowskie [do_narrow](../standard-library/ctype-class.md#do_narrow) i [do_widen](../standard-library/ctype-class.md#do_widen) kopiowanie elementów niezmieniony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [facet — klasa](http://msdn.microsoft.com/Library/dd4f12f5-cb1b-457f-af56-2fb204216ec1)   
 [ctype_base — klasa](../standard-library/ctype-base-class.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

