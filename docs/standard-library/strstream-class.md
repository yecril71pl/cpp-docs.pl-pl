---
title: "strstream — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6b8bef6b9ae2f4000adf620e2f898113b565f2a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="strstream-class"></a>strstream — Klasa
Zawiera opis obiektu, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```
class strstream : public iostream
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przechowuje obiekt klasy `strstreambuf`.  
  
> [!NOTE]
>  Ta klasa jest przestarzały. Należy rozważyć użycie [stringstream](../standard-library/sstream-typedefs.md#stringstream) lub [wstringstream](../standard-library/sstream-typedefs.md#wstringstream) zamiast tego.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[strstream](#strstream)|Tworzy obiekt typu `strstream`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Blokowanie](#freeze)|Powoduje, że jest niedostępna za pośrednictwem operacji buforu strumienia buforu strumienia.|  
|[pcount](#pcount)|Zwraca liczbę z liczbą elementów zapisywane w kontrolowanej sekwencji.|  
|[rdbuf](#rdbuf)|Zwraca wskaźnik do strumienia powiązanych `strstreambuf` obiektu.|  
|[str](#str)|Wywołania [Zablokuj](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<strstream — >  
  
 **Namespace:** Standard  
  
##  <a name="freeze"></a>  strstream::FREEZE  
 Powoduje, że jest niedostępna za pośrednictwem operacji buforu strumienia buforu strumienia.  
  
```
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>Parametry  
 `_Freezeit`  
 A `bool` wskazującą, czy ma strumień jest zablokowana.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).  
  
### <a name="example"></a>Przykład  
  Zobacz [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) na przykład, który używa **Zablokuj**.  
  
##  <a name="pcount"></a>  strstream::pcount  
 Zwraca liczbę z liczbą elementów zapisywane w kontrolowanej sekwencji.  
  
```
streamsize pcount() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów zapisywane w kontrolowanej sekwencji.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).  
  
### <a name="example"></a>Przykład  
  Zobacz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) przykładowe przy użyciu pcount.  
  
##  <a name="rdbuf"></a>  strstream::rdbuf  
 Zwraca wskaźnik do obiektu skojarzone strstreambuf — strumienia.  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do strumienia powiązanych strstreambuf — obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca adres buforu strumienia przechowywanych typu **wskaźnika** do [strstreambuf —](../standard-library/strstreambuf-class.md).  
  
### <a name="example"></a>Przykład  
  Zobacz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu korzystającego z `rdbuf`.  
  
##  <a name="str"></a>  strstream::str  
 Wywołania [Zablokuj](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.  
  
```
char *str();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do początku kontrolowanej sekwencji.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).  
  
### <a name="example"></a>Przykład  
  Zobacz [strstreambuf::str](../standard-library/strstreambuf-class.md#str) dla przykładu korzystającego z **str**.  
  
##  <a name="strstream"></a>  strstream::strstream  
 Tworzy obiekt typu `strstream`.  
  
```
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Rozmiar buforu.  
  
 `_Mode`  
 Tryb wejściowymi i wyjściowymi buforu. Zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Aby uzyskać więcej informacji.  
  
 `ptr`  
 Bufor.  
  
### <a name="remarks"></a>Uwagi  
 Oba konstruktory zainicjowanie klasy głównej przez wywołanie metody [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**), gdzie **sb** jest przechowywane obiekt klasy [strstreambuf —](../standard-library/strstreambuf-class.md) . Pierwszy Konstruktor inicjuje również **sb** przez wywołanie metody [strstreambuf —](../standard-library/strstreambuf-class.md#strstreambuf). Drugi Konstruktor inicjuje klasy podstawowej, jeden z dwóch sposobów:  
  
-   Jeśli `_Mode`  &  **ios_base::app**== 0, następnie `ptr` musi wyznaczyć pierwszy element tablicy `count` elementów i wywołania konstruktora `strstreambuf`( `ptr`, `count`, `ptr`).  
  
-   W przeciwnym razie `ptr` musi wyznaczyć pierwszy element tablicy liczba elementów zawierający parametry C których pierwszy element określony przez `ptr`i wywołania konstruktora `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).  
  
## <a name="see-also"></a>Zobacz też  
 [iostream](../standard-library/istream-typedefs.md#iostream)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)



