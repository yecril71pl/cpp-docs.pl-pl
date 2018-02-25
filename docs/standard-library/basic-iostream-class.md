---
title: "basic_iostream — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
dev_langs:
- C++
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 95912a24f3283e66a7f50c06999cf410f428defc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="basiciostream-class"></a>basic_iostream — Klasa
Klasy strumienia, który można wykonać obie czynności danych wejściowych i wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_iostream : public basic_istream<Elem, Tr>,  
    public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};  
```  
  
## <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje obiekt, który kontroluje wstawienia za pośrednictwem swojej klasy podstawowej [basic_ostream —](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`>, a ekstrakcje za pośrednictwem swojej klasy podstawowej [basic_ IStream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`>. Dwa obiekty współużytkują wspólne wirtualna klasa podstawowa [basic_ios —](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>. Również zarządzać wspólnej buforu strumienia, elementami typu `Elem`, którego cech znaków są określane przez klasę `Tr`. Konstruktor inicjuje jej klas podstawowych za pośrednictwem `basic_istream`( **strbuf**) i `basic_ostream`( **strbuf**).  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[basic_iostream](#basic_iostream)|Utwórz `basic_iostream` obiektu.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[swap](#swap)|Zamienia zawartość dostarczonego `basic_iostream` obiektu dla zawartości tego obiektu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator=](#op_eq)|Przypisuje wartość określonej `basic_iostream` obiektu do tego obiektu. Jest to dotyczące przypisania przenoszenia `rvalue` który nie pozostawione kopii.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<istream >  
  
 **Namespace:** Standard  
  
##  <a name="basic_iostream"></a>  basic_iostream::basic_iostream  
 Utwórz `basic_iostream` obiektu.  
  
```  
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```  
  
### <a name="parameters"></a>Parametry  
 `strbuf`  
 Istniejące `basic_streambuf` obiektu.  
  
 `right`  
 Istniejące `basic_iostream` obiekt, który jest używany do tworzenia nowego `basic_iostream`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje obiektów podstawowych poprzez `basic_istream(strbuf)` i `basic_ostream(strbuf)`.  
  
 Drugi Konstruktor inicjuje obiektów podstawowych, wywołując `move(right)`.  
  
##  <a name="op_eq"></a>  basic_iostream::operator =  
 Przypisz wartość określonej `basic_iostream` obiektu do tego obiektu. Jest to przypisania przenoszenia, obejmujące r-wartości nie pozostawione kopii.  
  
```  
basic_iostream& operator=(basic_iostream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `rvalue` Odwołanie do `basic_iostream` obiektu w celu przypisania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania operator elementu członkowskiego `swap(right)`.  
  
##  <a name="swap"></a>  basic_iostream::swap  
 Zamienia zawartość dostarczonego `basic_iostream` obiektu dla zawartości tego obiektu.  
  
```  
void swap(basic_iostream& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `basic_iostream` Obiektu można zamienić.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich `swap(right)`.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)

