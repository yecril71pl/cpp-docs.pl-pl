---
title: pin_ptr (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
dev_langs:
- C++
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afc99a352e0bde7918cab460293ff23061377551
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880169"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)
Deklaruje *przypiętego wskaźnika*, która jest używana tylko z środowisko uruchomieniowe języka wspólnego.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych.)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 (Ta funkcja językowa nie jest obsługiwana w środowisku wykonawczym systemu Windows).  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 A *przypiętego wskaźnika* jest wskaźnik wewnętrzny, który uniemożliwia obiektu wskazywana z przejściem stosu zebranego przez pamięci. Oznacza to, że wartość wskaźnika przypinania nie zostanie zmieniona przez środowisko uruchomieniowe języka wspólnego. Jest to wymagane, jeśli adres zarządzanej klasy do funkcji niezarządzanej tak, aby adres nie zmieni się nieoczekiwanie podczas rozpoznawania wywołania funkcji niezarządzanej.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;  
```  
  
### <a name="parameters"></a>Parametry  
 *cv_qualifier*  
 `const` lub `volatile` kwalifikatorów. Domyślnie jest przypięty wskaźnik `volatile`. Jest nadmiarowy, ale nie jest błąd, aby zadeklarować przypiętego wskaźnika `volatile`.  
  
 *Typ*  
 Typ `initializer`.  
  
 *var*  
 Nazwa `pin_ptr` zmiennej.  
  
 *initializer*  
 Element członkowski typu referencyjnego, element tablicy zarządzanej lub inny obiekt, który można przypisać do wskaźnika natywnego.  
  
### <a name="remarks"></a>Uwagi  
 A `pin_ptr` reprezentuje podzbiorem funkcji wskaźnik natywny. W związku z tym wszystkie elementy, które można przypisać na wskaźnik natywny można również przypisać do `pin_ptr`. Wskaźnik wewnętrzny może wykonać ten sam zestaw operacji jako wskaźników natywnych, w tym porównania i arytmetyka wskaźnika.  
  
 Obiekt lub obiekt podrzędny zarządzanej klasy można przypiąć, w którym to przypadku środowisko uruchomieniowe języka wspólnego nie przeniesie go podczas wyrzucania elementów bezużytecznych. Użycie podmiotu zabezpieczeń jest wskaźnikiem do danych zarządzanych jako rzeczywisty parametr wywołania funkcji niezarządzanej. Podczas cyklu zbierania środowisko wykonawcze będzie przeprowadzał inspekcję metadanych utworzone dla przypiętego wskaźnika i nie zostanie przesunięty w elemencie, który wskazuje.  
  
 Przypinanie obiektu przypięcie jego pola wartości; oznacza to pól typów pierwotnych lub wartości typu. Jednak pola deklarowana przez śledzenie uchwytu (`%`) nie jest przypięty.  
  
 Przypinanie obiektu podrzędnego zdefiniowaną w obiekcie zarządzanych skutkuje przypinanie całego obiektu.  
  
 Jeśli przypięty wskaźnik jest ponownie przypisywane, aby wskazywał nową wartość, poprzednie wystąpienie wskazywał przestaje być uważany za przypięty.  
  
 Obiekt jest przypięty tylko podczas `pin_ptr` punktów do niego. Obiekt jest już przypięty podczas jego przypiętego wskaźnika wykracza poza zakres lub ma wartość [nullptr](../windows/nullptr-cpp-component-extensions.md). Po `pin_ptr` zbliża się poza zakresem, obiekt, który został przypięty można przenieść na stercie przez moduł garbage collector. Natywnymi wskaźnikami, które nadal wskaż obiekt nie będzie aktualizowana i zwalnia odwołujące się do jednego z nich mogą budzić wystąpił nieodwracalny wyjątek.  
  
 Jeśli nie unieruchamiania wskaźników wskaż obiekt (wszystkie unieruchamiania wskaźników poszło poza zakresem, zostały przypisane do punktu z innymi obiektami lub zostały przypisane [nullptr](../windows/nullptr-cpp-component-extensions.md)), obiekt pewno nie jest przypięty.  
  
 Przypiętego wskaźnika może wskazywać do dojścia odwołania, typu wartości lub dojście do typu opakowanego, elementu członkowskiego typu zarządzanego lub element tablicy zarządzanej. Nie może wskazywać typ referencyjny.  
  
 Pobieranie adresu `pin_ptr` że wskazuje obiekt natywny powoduje niezdefiniowane zachowanie.  
  
 Unieruchamiania wskaźników mogą być deklarowane jako zmienne lokalne niestatyczna na stosie.  
  
 Nie można użyć unieruchamiania wskaźników jako:  
  
-   parametry funkcji  
  
-   zwracany typ funkcji  
  
-   element członkowski klasy  
  
-   Typ docelowy rzutowanie.  
  
 `pin_ptr` Trwa `cli` przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [platformy, domyślna i cli przestrzenie nazw](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).  
  
 Aby uzyskać więcej informacji o wewnętrznych wskaźników, zobacz [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md).  
  
 Aby uzyskać więcej informacji na temat Unieruchamianie wskaźników, zobacz [jak: numer Pin wskaźników oraz tablic](../windows/how-to-pin-pointers-and-arrays.md) i [jak: deklarowanie Unieruchamianie wskaźników i typów wartości](../windows/how-to-declare-pinning-pointers-and-value-types.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W poniższym przykładzie użyto `pin_ptr` Aby ograniczyć położenie pierwszego elementu tablicy.  
  
```  
// pin_ptr_1.cpp  
// compile with: /clr   
using namespace System;  
#define SIZE 10  
  
#pragma unmanaged  
// native function that initializes an array  
void native_function(int* p) {  
   for(int i = 0 ; i < 10 ; i++)  
    p[i] = i;  
}  
#pragma managed  
  
public ref class A {  
private:  
   array<int>^ arr;   // CLR integer array  
  
public:  
   A() {  
      arr = gcnew array<int>(SIZE);  
   }  
  
   void load() {  
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr  
   int* np = p;   // pointer to the first element in arr  
   native_function(np);   // pass pointer to native function  
   }  
  
   int sum() {  
      int total = 0;  
      for (int i = 0 ; i < SIZE ; i++)  
         total += arr[i];  
      return total;  
   }  
};  
  
int main() {  
   A^ a = gcnew A;  
   a->load();   // initialize managed array using the native function  
   Console::WriteLine(a->sum());  
}  
```  
  
 **Output**  
  
```Output  
45  
```  
  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że można przekonwertować wskaźnik wewnętrzny do przypiętego wskaźnika i że zwracany typ funkcji address-of — operator (`&`) jest wskaźnik wewnętrzny, gdy argument jest na stercie zarządzanej.  
  
```  
// pin_ptr_2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   G() : i(1) {}  
   int i;  
};  
  
ref struct H {  
   H() : j(2) {}  
   int j;  
};  
  
int main() {  
   G ^ g = gcnew G;   // g is a whole reference object pointer  
   H ^ h = gcnew H;  
  
   interior_ptr<int> l = &(g->i);   // l is interior pointer  
  
   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer  
  
   k = l;   // ok  
   Console::WriteLine(*k);  
};  
```  
  
 **Output**  
  
```Output  
1  
```  
  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że mogą być rzutowane przypiętego wskaźnika do innego typu.  
  
```  
// pin_ptr_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class ManagedType {  
public:  
   int i;  
};  
  
int main() {  
   ManagedType ^mt = gcnew ManagedType;  
   pin_ptr<int> pt = &mt->i;  
   *pt = 8;  
   Console::WriteLine(mt->i);  
  
   char *pc = ( char* ) pt;  
   *pc = 255;  
   Console::WriteLine(mt->i);  
}  
```  
  
 **Output**  
  
```Output  
8  
255  
```