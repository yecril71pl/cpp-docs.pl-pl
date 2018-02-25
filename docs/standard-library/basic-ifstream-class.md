---
title: "basic_ifstream — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9c923d4c3de5410ac65f9706d875300b0d07cbb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="basicifstream-class"></a>basic_ifstream — Klasa
Zawiera opis obiektu, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, elementami typu `Elem`, którego znak cechy są określane przez klasę `Tr`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ifstream : public basic_istream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 Podstawowy element buforu plików.  
  
 `Tr`  
 Cechy podstawowy element pliku buforu (zazwyczaj `char_traits` <  `Elem`>).  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przechowuje obiekt klasy `basic_filebuf` <  `Elem`, `Tr`>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób odczytywania tekstu z pliku.  
  
```  
// basic_ifstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_class.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
## <a name="input-basicifstreamclasstxt"></a>Dane wejściowe: basic_ifstream_class.txt  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[basic_ifstream](#basic_ifstream)|Inicjuje nowe wystąpienie klasy `basic_ifstream` obiektu.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[close](#close)|Zamyka plik.|  
|[is_open](#is_open)|Określa, czy plik jest otwarty.|  
|[open](#open)|Otwiera plik.|  
|[rdbuf](#rdbuf)|Zwraca adres buforu przechowywanych strumienia.|  
|[swap](#swap)|Zamienia zawartość tego `basic_ifstream` zawartości dotyczącej dostępnego `basic_ifstream`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator=](#op_eq)|Przypisuje zawartości tego obiektu strumienia. Jest to dotyczące przypisania przenoszenia `rvalue` który nie pozostawione kopii.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<fstream — >  
  
 **Namespace:** Standard  
  
##  <a name="basic_ifstream"></a>  basic_ifstream::basic_ifstream  
 Tworzy obiekt typu `basic_ifstream`.  
  
```  
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filename`  
 Nazwa pliku, aby otworzyć.  
  
 `_Mode`  
 Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Domyślny plik otwierania ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [basic_istream —](../standard-library/basic-istream-class.md)( `sb`), gdzie `sb` jest przechowywane obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. Inicjuje również `sb` przez wywołanie metody `basic_filebuf` <  `Elem`, `Tr`>.  
  
 Konstruktory drugiego i trzeciego inicjuje klasy podstawowej, przez wywołanie metody `basic_istream`( `sb`). Inicjuje również `sb` przez wywołanie metody [basic_filebuf —](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>, następnie `sb`. [Otwórz](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::in`). Jeśli funkcja ostatnie zwraca wskaźnika o wartości null, Konstruktor wywołuje **metoda setstate**( `failbit`).  
  
 Czwarty Konstruktor inicjuje obiekt z zawartością `right`, traktowane jako odwołanie do r-wartości.  
  
### <a name="example"></a>Przykład  
  Poniższy przykład przedstawia sposób odczytywania tekstu z pliku. Aby utworzyć plik, zobacz przykład [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).  
  
```  
// basic_ifstream_ctor.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_ctor.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
##  <a name="close"></a>  basic_ifstream::Close  
 Zamyka plik.  
  
```  
void close();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich [rdbuf](#rdbuf)  **->**  [zamknąć](../standard-library/basic-filebuf-class.md#close).  
  
### <a name="example"></a>Przykład  
  Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który używa **zamknąć**.  
  
##  <a name="is_open"></a>  basic_ifstream::is_open  
 Określa, czy plik jest otwarty.  
  
```  
bool is_open() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli plik jest otwarty, **false** inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [rdbuf](#rdbuf)  **->**  [is_open](../standard-library/basic-filebuf-class.md#is_open).  
  
### <a name="example"></a>Przykład  
  Zobacz [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) na przykład, który używa `is_open`.  
  
##  <a name="open"></a>  basic_ifstream::Open  
 Otwiera plik.  
  
```  
void open(
    const char* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,  
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filename`  
 Nazwa pliku, aby otworzyć.  
  
 `_Mode`  
 Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Domyślny plik otwierania ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich [rdbuf](#rdbuf)  **->**  [Otwórz](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; **ios_base::in**). Jeśli otwarty zakończy się niepowodzeniem, wywołania funkcji [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**), który może zgłaszać wyjątek ios_base::failure.  
  
### <a name="example"></a>Przykład  
  Zobacz [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) na przykład, który używa **Otwórz**.  
  
##  <a name="op_eq"></a>  basic_ifstream::operator =  
 Przypisuje zawartości tego obiektu strumienia. Jest to przypisania przenoszenia, obejmujące r-wartości nie pozostawione kopii.  
  
```  
basic_ifstream& operator=(basic_ifstream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odwołania do r-wartości do `basic_ifstream` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `*this`.  
  
### <a name="remarks"></a>Uwagi  
 Operator członkowski zastępuje zawartość obiektu przy użyciu zawartości `right`, traktowane jako odwołanie do r-wartości. Aby uzyskać więcej informacji, zobacz [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).  
  
##  <a name="rdbuf"></a>  basic_ifstream::rdbuf  
 Zwraca adres buforu przechowywanych strumienia.  
  
```  
basic_filebuf<Elem, Tr> *rdbuf() const 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [basic_filebuf —](../standard-library/basic-filebuf-class.md) obiekt reprezentujący buforu przechowywanych strumienia.  
  
### <a name="example"></a>Przykład  
  Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który używa `rdbuf`.  
  
##  <a name="swap"></a>  basic_ifstream::swap  
 Zamienia zawartość dwóch `basic_ifstream` obiektów.  
  
```  
void swap(basic_ifstream& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odwołanie do innego buforu strumienia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska wymiany zawartość obiektu zawartość `right`.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)


