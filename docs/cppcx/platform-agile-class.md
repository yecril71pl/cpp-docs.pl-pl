---
title: Klasa platform::Agile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
dev_langs: C++
helpviewer_keywords: Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 4acb38dc8619123fe2f0640366e506f77993edb2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformagile-class"></a>Klasa platform::Agile
Reprezentuje obiekt, który ma MashalingBehavior = Standard jako obiekt agile, znacznie ogranicza prawdopodobieństwo wątkowość wyjątków w czasie wykonywania. `Agile<T>` Umożliwia-agile obiektu połączeń telefonicznych, lub można wywołać z tym samym lub innym wątku. Aby uzyskać więcej informacji, zobacz [wątków i przekazywanie](../cppcx/threading-and-marshaling-c-cx.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <typename T>  
class Agile;  
```  
  
#### <a name="parameters"></a>Parametry  
 T  
 Właściwość typename klasy elastyczne.  
  
### <a name="remarks"></a>Uwagi  
 Większość klas w środowisku wykonawczym systemu Windows to elastyczne. Obiekt agile można wywołać lub wywołana przez obiekt wewnątrzprocesową lub poza procesem, w tym samym lub innym wątku. Jeśli obiekt nie jest agile, zawijać-agile obiektu w `Agile<T>` obiektu, który jest elastyczne. Następnie przy użyciu `Agile<T>` obiektu mogą być przekazywane, i mogą być używane-agile obiektu źródłowego.  
  
 `Agile<T>` Klasa jest klasą macierzystego, standard C++ i wymaga `agile.h`. Reprezentuje obiekt agile i elastyczne obiektu *kontekstu*. Kontekst określa model wątkowości i zachowanie marshalingu agile obiektu. System operacyjny używa kontekstu do określenia sposobu zorganizowania obiektu.  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Agile::Agile](#ctor)|Inicjuje nowe wystąpienie klasy elastyczne.|  
|[Elastyczne:: ~ Agile — destruktor](#dtor)|Niszczy bieżące wystąpienie klasy elastyczne.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Agile::Get](#get)|Zwraca uchwyt do obiektu reprezentowanego przez bieżący obiekt elastyczne.|  
|[Agile::GetAddressOf](#getaddressof)|Ponownie inicjuje bieżącego obiektu Agile, a następnie zwraca adres dojścia do typu obiektu `T`.|  
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Zwraca adres uchwyt do obiektu reprezentowanego przez bieżący obiekt elastyczne.|  
|[Agile::Release](#release)|Usuwa obiekt bieżącego obiektu Agile i kontekstu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Agile::operator ->](#operator-arrow)|Pobiera dojścia do obiektu reprezentowanego przez bieżący obiekt elastyczne.|  
|[Agile::operator =](#operator-assign)|Przypisuje określona wartość, jak bieżący obiekt Agile.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Object`  
  
 `Agile`  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Nagłówek:** agile.h  

## <a name="ctor"></a>Konstruktor Agile::Agile
Inicjuje nowe wystąpienie klasy elastyczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
 Agile();  
  
Agile(T^ object);   
  
Agile(const Agile<T>& object);  
  
Agile(Agile<T>&& object);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ określony przez parametr typename szablonu.  
  
 `object`  
 W drugiej wersji tego konstruktora obiekt służący do inicjuje nowe wystąpienie Agile. W trzecim wersja obiektu, który jest skopiowany do nowego wystąpienia elastyczne. W czwartym wersja obiektu, który jest przenoszona do nowego wystąpienia elastyczne.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję tego konstruktora jest konstruktora domyślnego. Druga wersja inicjuje nową klasę wystąpienia Agile z obiekt określony przez `object` parametru. Trzeci wersja jest Konstruktor kopiujący. Wersja czwarty jest konstruktor przenoszenia. Ten konstruktor nie zgłaszają wyjątki.  

## <a name="dtor"></a>Elastyczne:: ~ Agile — destruktor
Niszczy bieżące wystąpienie klasy elastyczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
~Agile();  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten destruktor zwalnia również obiektu reprezentowanego przez bieżący obiekt elastyczne.  
  
## <a name="get"></a>Agile::Get — metoda
Zwraca uchwyt do obiektu reprezentowanego przez bieżący obiekt elastyczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
   T^ Get() const  
;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do obiektu reprezentowanego przez bieżący obiekt elastyczne.  
  
 Typ wartości zwracanej jest rzeczywiście niejawne typów wewnętrznych. Wygodny sposób do przechowywania wartości zwracanej jest aby przypisać go do zmiennej, która jest zadeklarowana za pomocą **automatycznie** wpisz wnioskowanie — słowo kluczowe. Na przykład `auto x = myAgileTvariable->Get();`.  
  
## <a name="getaddressof"></a>Agile::GetAddressOf — metoda
Ponownie inicjuje bieżącego obiektu Agile, a następnie zwraca adres dojścia do typu obiektu `T`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
T^* GetAddressOf()   
throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ określony przez parametr typename szablonu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres dojścia do typu obiektu `T`.  
  
### <a name="remarks"></a>Uwagi  
 Ta operacja zwalnia reprezentacja bieżącego obiektu typu `T`, jeśli występują; ponownie inicjuje obiekt elastyczne elementy członkowskie danych; uzyskuje bieżącego kontekstu wątkowości; a następnie zwraca adresu zmiennej uchwyt do obiektu, mogącej reprezentować agile obiektu. Aby spowodować wystąpienie klasy Agile do reprezentowania obiektu, użyj operatora przypisania ([Agile::operator =](#operator-assign)) można przypisać obiektu wystąpienia klasy Agile.  

## <a name="getaddressofforinout"></a>Agile::GetAddressOfForInOut — metoda
Zwraca adres uchwyt do obiektu reprezentowanego przez bieżący obiekt elastyczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
T^* GetAddressOfForInOut()  throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ określony przez parametr typename szablonu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres dojścia do obiektu reprezentowanego przez bieżący obiekt elastyczne.  
  
### <a name="remarks"></a>Uwagi  
 Ta operacja uzyskuje bieżącego kontekstu wątków, a następnie zwraca adres uchwyt do obiektu źródłowego.  

## <a name="release"></a>Agile::Release — metoda
Usuwa obiekt bieżącego obiektu Agile i kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
void Release() throw();  
  
```  
  
### <a name="remarks"></a>Uwagi  
 Bieżący obiekt Agile obiektu źródłowego i kontekstu są odrzucane, jeśli istnieją, a następnie Agile obiektu ma wartość null.  

## <a name="operator-arrow"></a>Agile::operator —&gt; — Operator
Pobiera dojścia do obiektu reprezentowanego przez bieżący obiekt elastyczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
T^ operator->()   
const throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do obiektu reprezentowanego przez bieżący obiekt elastyczne.  
  
 Zwraca faktycznie niejawne typów wewnętrznych. Wygodny sposób do przechowywania wartości zwracanej jest aby przypisać go do zmiennej, która jest zadeklarowana za pomocą **automatycznie** wpisz wnioskowanie — słowo kluczowe.  

## <a name="operator-assign"></a>Agile::operator = — Operator
Przypisuje określony obiekt do bieżącego obiektu elastyczne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
   Agile<T> operator=(T^ object) throw();  
  
   Agile<T> operator=(  
      const Agile<T>& object  
) throw();  
  
   Agile<T> operator=(  
      Agile<T>&& object  
) throw();  
  
   T^ operator=(  
      IUnknown* lp  
) throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ określony przez właściwość typename szablonu.  
  
 `object`  
 Obiekt lub uchwyt do obiektu, który jest kopiowany lub przenieść do bieżącego obiektu Agile.  
  
 `lp`  
 Wskaźnik interfejsu IUnknown obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do typu obiektu`T`  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję operatora przypisania kopiuje dojścia do typu odwołania, jak bieżący obiekt elastyczne. Drugi kopii wersji odwołania do Agile wpisz jak bieżący obiekt elastyczne. Trzeci wersji przenosi wpisz Agile do bieżącego obiektu elastyczne. Wersja czwarty przesuwa kursor do obiektu COM, jak bieżący obiekt elastyczne.  
  
 Operacja przypisania utrzymuje automatycznie kontekście bieżącego obiektu elastyczne. 
       
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](platform-namespace-c-cx.md)