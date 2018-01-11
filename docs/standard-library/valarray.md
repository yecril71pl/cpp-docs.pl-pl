---
title: "&lt;valarray —&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <valarray>
dev_langs: C++
helpviewer_keywords: valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 917dfbf870959b6934eaa49cbaab05e27304fb77
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltvalarraygt"></a>&lt;valarray —&gt;
Definiuje valarray — klasa szablonu i wiele pomocniczych szablonu klasy i funkcje.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <valarray>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Te klasy szablonu i funkcje są dozwolone nietypowe współrzędnych w celu lepszą wydajność. W szczególności dowolnej funkcji zwracających typ **valarray —\<**T1 **>**  może zwracać obiekt innego typu T2. W takim przypadku funkcji, które akceptuje jeden lub więcej argumentów typu **valarray —\<**T2 **>**  musi mieć przeciążeń, które akceptuje dowolne kombinacje tych argumentów, każdy argument typu T2 zastąpione.  
  
### <a name="functions"></a>Funkcje  
  
|||  
|-|-|  
|[ABS](../standard-library/valarray-functions.md#abs)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe wartość bezwzględną liczby elementów wejściowych valarray —.|  
|[ACOS](../standard-library/valarray-functions.md#acos)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe arcus cosinus liczby elementów wejściowych valarray —.|  
|[ASIN](../standard-library/valarray-functions.md#asin)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe arcus sinus elementów wejściowych valarray —.|  
|[ATAN](../standard-library/valarray-functions.md#atan)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe wartość główną arcus tangens elementów wejściowych valarray —.|  
|[ATAN2](../standard-library/valarray-functions.md#atan2)|Zwraca valarray —, której elementy są równe arcus tangens kartezjańskimi określone przez kombinację stałych i elementy valarrays składników.|  
|[COS](../standard-library/valarray-functions.md#cos)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe cosinus elementów wejściowych valarray —.|  
|[COSH](../standard-library/valarray-functions.md#cosh)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe cosinus hiperboliczny elementów wejściowych valarray —.|  
|[EXP](../standard-library/valarray-functions.md#exp)|Działa na elementy wejściowe valarray zwracanie valarray —, której elementy są równe wykładniczej elementów wejściowych valarray — naturalnego —.|  
|[Dziennik](../standard-library/valarray-functions.md#log)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe logarytm naturalny elementów wejściowych valarray —.|  
|[LOG10](../standard-library/valarray-functions.md#log10)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są takie same na podstawie 10 lub logarytmu elementów wejściowych valarray —.|  
|[Pow](../standard-library/valarray-functions.md#pow)|Działa w przypadku elementów wejściowych valarrays i stałe, zwracając valarray —, której elementy są równe podstawowej określone przez elementy wejściowe valarray — lub stałą podniesionej do potęgi określonej przez elementy wejściowe valarray — lub stała.|  
|[SIN](../standard-library/valarray-functions.md#sin)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe sinus elementów wejściowych valarray —.|  
|[SINH](../standard-library/valarray-functions.md#sinh)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe sinus hiperboliczny liczby elementów wejściowych valarray —.|  
|[SQRT](../standard-library/valarray-functions.md#sqrt)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe pierwiastek kwadratowy liczby elementów wejściowych valarray —.|  
|[swap](../standard-library/valarray-functions.md#swap)||  
|[tan](../standard-library/valarray-functions.md#tan)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe tangens elementów wejściowych valarray —.|  
|[TANH](../standard-library/valarray-functions.md#tanh)|Działa na elementy wejściowe valarray —, zwracając valarray —, której elementy są równe tangens hiperboliczny liczby elementów wejściowych valarray —.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator!=](../standard-library/valarray-operators.md#op_neq)|Sprawdza, czy są odpowiednie elementy dwóch valarrays równej wielkości nierównej lub czy są równe wszystkie elementy valarray — określona wartość valarray — typ elementu.|  
|[% — operator](../standard-library/valarray-operators.md#op_mod)|Uzyskuje resztę z dzielenia odpowiednie elementy dwóch valarrays równej wielkości lub podzielenie valarray — przez określoną wartość typu elementu valarray — lub podziału przez valarray — określona wartość.|  
|[Operator &](../standard-library/valarray-operators.md#op_amp)|Uzyskuje operatora testu koniunkcji **i** między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość typu elementu.|  
|[Operator & &](../standard-library/valarray-operators.md#op_amp_amp)|Uzyskuje logicznym **i** między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość valarray — typ elementu.|  
|[operator >](../standard-library/valarray-operators.md#op_gt)|Sprawdza, czy elementy jeden valarray — są większe niż elementów równej wielkości valarray — lub czy wszystkie elementy valarray — większa lub mniejsza niż określona wartość valarray — typ elementu.|  
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Sprawdza, czy elementy jeden valarray — są większe niż lub równe elementów równej wielkości valarray — lub czy wszystkie elementy valarray — są większe niż lub równe lub mniejsze niż lub równa określonej wartości.|  
|[operator >>](../standard-library/valarray-operators.md#op_gt_gt)|Prawo zmian usługi bits dla każdego elementu valarray — określonej liczby miejsc lub element-wise wartość określoną w drugim valarray —.|  
|[Operator <](../standard-library/valarray-operators.md#op_lt)|Sprawdza, czy elementy valarray — co jest mniejsza od elementów równej wielkości valarray — lub czy wszystkie elementy valarray — większa lub mniejsza niż określona wartość.|  
|[Operator < =](../standard-library/valarray-operators.md#op_lt_eq)|Sprawdza, czy elementy jeden valarray — są mniejsze niż lub równe elementów równej wielkości valarray — lub czy wszystkie elementy valarray — są większe niż lub równe lub mniejsze niż lub równa określonej wartości.|  
|[Operator <<](../standard-library/valarray-operators.md#op_lt_lt)|Po lewej wykonuje przesunięcie bitów dla każdego elementu valarray — określonej liczby miejsc lub element-wise wartość określoną w drugim valarray —.|  
|[operator *](../standard-library/valarray-operators.md#op_star)|Uzyskuje element-wise produktu między elementami odpowiedniego dwóch valarrays równej wielkości typu lub między valarray — określona wartość valarray — typ elementu.|  
|[operator +](../standard-library/valarray-operators.md#op_add)|Uzyskuje element-wise Suma między elementami odpowiedniego dwóch valarrays równej wielkości typu lub między valarray — określona wartość valarray — typ elementu.|  
|[operator-](../standard-library/valarray-operators.md#operator-)|Uzyskuje element-wise różnica między odpowiednie elementy tego dwa valarrays równej wielkości lub między valarray — określona wartość valarray — typ elementu.|  
|[operator /](../standard-library/valarray-operators.md#op_div)|Uzyskuje element-wise iloraz między elementami odpowiedniego dwóch valarrays równej wielkości typu lub między valarray — określona wartość valarray — typ elementu.|  
|[operator ==](../standard-library/valarray-operators.md#op_eq_eq)|Testy, czy są odpowiednie elementy dwóch valarrays równej wielkości większy lub czy są wszystkie elementy valarray — równa określonej wartości typu elementu valarray —.|  
|[operator ^](../standard-library/valarray-operators.md#op_xor)|Uzyskuje operator wyłączny `OR` między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość typu elementu.|  
|[Operator &#124;](../standard-library/valarray-operators.md#op_or)|Uzyskuje operatora testu koniunkcji `OR` między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość typu elementu.|  
|[Operator &#124; &#124;](../standard-library/valarray-operators.md#op_lor)|Uzyskuje logicznym `OR` między odpowiednie elementy dwóch valarrays równej wielkości lub valarray — i określoną wartość valarray — typ elementu.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[gslice, klasa](../standard-library/gslice-class.md)|Klasa narzędzia valarray —, który służy do definiowania wielowymiarowych wycinków valarray —.|  
|[gslice_array, klasa](../standard-library/gslice-array-class.md)|Klasy wewnętrzne, pomocnicze szablonu, która obsługuje obiekty ogólne wycinek zapewniając operacji między macierzami z podzbioru zdefiniowanych przez ogólne wycinek valarray —.|  
|[indirect_array, klasa](../standard-library/indirect-array-class.md)|Klasy wewnętrzne, pomocnicze szablonu, która obsługuje obiekty, które są podzbiorem valarrays zapewniając operacji między macierzami podzbioru zdefiniowanych przez określenie podzbiór indeksów valarray — nadrzędnego.|  
|[mask_array, klasa](../standard-library/mask-array-class.md)|Klasy wewnętrzne, pomocnicze szablonu, która obsługuje obiekty, które są podzbiorem valarrays nadrzędnego określić z wyrażenie logiczne, wprowadzając operacji między macierzami podzbioru.|  
|[slice, klasa](../standard-library/slice-class.md)|Klasa narzędzia valarray —, który służy do definiowania jednowymiarowa, vector przypominającej podzbiór valarray —.|  
|[slice_array, klasa](../standard-library/slice-array-class.md)|Klasy wewnętrzne, pomocnicze szablonu, która obsługuje obiekty wycinek zapewniając operacji między macierzami z podzbioru zdefiniowanych przez wycinka valarray —.|  
|[valarray, klasa](../standard-library/valarray-class.md)|Klasa szablonu opisuje obiekt, który określa sekwencję elementów typu **typu** który są przechowywane w postaci tablicy i przeznaczone do wykonywania operacji matematycznych o dużej szybkości, zoptymalizowana pod kątem wydajności obliczeniowej.|  
  
### <a name="specializations"></a>Specjalizacje  
  
|||  
|-|-|  
|[valarray —\<bool > — klasa](../standard-library/valarray-bool-class.md)|Specjalna wersja valarray — klasa szablonu\<**typu**> do elementów typu `bool`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



