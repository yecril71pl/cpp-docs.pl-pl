---
title: "Wartość typów (Modern C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d84888236b81fe862c6a22793e926ebf7df55c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="value-types-modern-c"></a>Typy wartości (Modern C++)
Klasy C++ są przez typy wartości domyślnej. Ten temat zawiera wstępne omówienie typów wartości i problemy dotyczące ich stosowania.  
  
## <a name="value-vs-reference-types"></a>Wartość, a typy odwołań  
 Jak wcześniej podane, klas C++ przez typy wartości domyślnej. Jako typów referencyjnych, umożliwiające polimorficznych zachowania do obsługi obiektowo programowania można określić ich. Typy wartości czasami są wyświetlane z punktu widzenia pamięci i układ formantu, typy referencyjne są o klasy podstawowe i funkcji wirtualnych do celów polimorficznym. Domyślnie typów wartości są copyable, co oznacza, że istnieje zawsze konstruktora kopiującego i operatora przypisania kopii. Dla typów odwołań wprowadzeniu klasy z systemem innym niż copyable (Wyłącz konstruktora kopiującego i operatora przypisania kopii) i używać destruktor wirtualny obsługujący ich polimorfizm zamierzone. Typy wartości są również dotyczące zawartości, które, gdy są one kopiowane zawsze zapewniają dwa niezależne wartości, które mogą być modyfikowane oddzielnie. Typy odwołań są o tożsamości — jest obiektem jakiego rodzaju? Z tego powodu "typy referencyjne" są też określane jako "typach polimorficznych".  
  
 Jeśli naprawdę chcesz typu typu odwołanie (klasa podstawowa, funkcji wirtualnych), musisz jawnie wyłączyć kopiowania, jak pokazano w `MyRefType` klasy w poniższym kodzie.  
  
```cpp  
// cl /EHsc /nologo /W4  
  
class MyRefType {  
private:  
    MyRefType & operator=(const MyRefType &);  
    MyRefType(const MyRefType &);  
public:  
    MyRefType () {}  
};  
  
int main()  
{  
    MyRefType Data1, Data2;  
    // ...  
    Data1 = Data2;  
}  
```  
  
 Kompilowanie kodu powyżej spowoduje następujący błąd:  
  
```Output  
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'  
        meow.cpp(5) : see declaration of 'MyRefType::operator ='  
        meow.cpp(3) : see declaration of 'MyRefType'  
  
```  
  
## <a name="value-types-and-move-efficiency"></a>Typy wartości i Przenieś wydajności  
 Narzut alokacji kopii unika się z powodu nowej kopii optymalizacji. Na przykład podczas wstawiania ciągu środku wektor ciągów nie będzie żadnych kopii Ponowna alokacja koszty tylko move - nawet wtedy, gdy jej wynikiem Zwiększaj wektora sam. Dotyczy to również inne operacje, na przykład wykonywania operacji dodawania dla dwóch bardzo dużych obiektów. Jak włączyć te wartości optymalizacje operację? W niektóre kompilatory C++ kompilator umożliwi to dla Ciebie niejawnie taki sam sposób, jak kopiowanie konstruktorów mogą być automatycznie generowane przez kompilator. Jednak w programie Visual C++ klasy należy "wyrazić zgodę na" Przenieś przypisania i konstruktorów przez zadeklarowanie go w definicji klasy. Jest to zrobić za pomocą podwójnego ampersand (& &) odwołania do wartości w właściwego członka działanie deklaracje i definiowanie Konstruktor przenoszenia i Przenieś metody przypisania.  Należy również wstawić prawidłowego kodu do "wykradać wnętrzności" poza obiekt źródłowy.  
  
 Jak można zdecydować, czy należy przenieść włączone? Jeśli już wiesz, należy skopiować konstrukcji włączone, prawdopodobnie chcesz przenieść włączone, jeśli może być tańsze niż bezpośrednich kopii. Jednak jeśli wiadomo, że należy przenieść pomocy technicznej, go nie musi oznaczać, że kopia włączone. Ostatnim przypadku będzie można wywołać "tylko do przeniesienia typu". Na przykład już w standardowej bibliotece `unique_ptr`. Jako notatka boczna stary `auto_ptr` jest przestarzałe i zostało zastąpione przez `unique_ptr` dokładnie z powodu braku obsługi semantyki przenoszenia w poprzedniej wersji języka C++.  
  
 Za pomocą semantyki przenoszenia można wartość zwracaną lub Wstaw w środku. Przeniesienie jest optymalizacji kopiowania. Istnieje potrzeba Alokacja sterty jako obejście tego problemu. Należy wziąć pod uwagę następujące pseudocode:  
  
```cpp  
#include <set>  
#include <vector>  
#include <string>  
using namespace std;  
  
//...  
set<widget> LoadHugeData() {  
    set<widget> ret;  
    // ... load data from disk and populate ret  
    return ret;  
}  
//...  
widgets = LoadHugeData();   // efficient, no deep copy  
  
vector<string> v = IfIHadAMillionStrings();  
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle  
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)  
//...  
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );  
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);  
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );  
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);  
//...  
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies  
```  
  
### <a name="enabling-move-for-appropriate-value-types"></a>Włączanie przenoszenia dla typów odpowiednie wartości  
 Dla klasy przypominającej wartość, gdzie przenoszenia może być tańsze niż bezpośrednich kopii Włącz konstrukcji przenoszenia i Przenieś przypisania w celu zwiększenia wydajności. Należy wziąć pod uwagę następujące pseudocode:  
  
```cpp  
#include <memory>  
#include <stdexcept>  
using namespace std;  
// ...  
class my_class {  
    unique_ptr<BigHugeData> data;  
public:  
    my_class( my_class&& other )   // move construction  
        : data( move( other.data ) ) { }  
    my_class& operator=( my_class&& other )   // move assignment  
    { data = move( other.data ); return *this; }  
    // ...  
    void method() {   // check (if appropriate)  
        if( !data )   
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");  
    }  
};  
  
```  
  
 Po włączeniu kopii konstrukcji/przypisania także włączyć przenoszenia konstrukcji/przypisania, jeśli jest tańsze niż bezpośrednich kopii.  
  
 Niektóre *bez wartości* typy Przenieś tylko, np. Jeśli nie można sklonować zasób tylko przeniesienia własności. Przykład: `unique_ptr`.  
  
## <a name="section"></a>Sekcja  
 Zawartość  
  
## <a name="see-also"></a>Zobacz też  
 [System typów języka C++](../cpp/cpp-type-system-modern-cpp.md)   
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)