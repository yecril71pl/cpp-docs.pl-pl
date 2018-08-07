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
ms.openlocfilehash: a87dadfd4787e4bd0100efb8fe7ffe2b1e7a8899
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607855"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)
Deklaruje *przypiętego wskaźnika*, która jest używana tylko w przypadku środowiska uruchomieniowego języka wspólnego.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 (Nie ma żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 (Ta funkcja języka nie jest obsługiwana w środowisku uruchomieniowym Windows).  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 A *przypiętego wskaźnika* jest posługiwanie się nimi wskaźnik, który uniemożliwia obiekt wskazywany przenoszenia na stercie zebranych elementów bezużytecznych. Oznacza to, że wartość wskaźnika przypinania nie zostanie zmieniona przez środowisko uruchomieniowe języka wspólnego. Jest to wymagane, jeśli przekazujesz adres klasy zarządzanej do niezarządzanej funkcji tak, aby adres nie zmieni się nieoczekiwanie podczas rozpoznawania wywołania funkcji niezarządzanej.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;  
```  
  
### <a name="parameters"></a>Parametry  
 *cv_qualifier*  
 **Const** lub **volatile** kwalifikatorów. Domyślnie jest przypięty wskaźnik **volatile**. Jest nadmiarowy, ale nie jest błąd, aby zadeklarować wskaźnik przypinania **volatile**.  
  
 *Typ*  
 Typ *inicjatora*.  
  
 *var*  
 Nazwa **pin_ptr** zmiennej.  
  
 *initializer*  
 Element członkowski typu odwołania, element tablicy zarządzanej lub inny obiekt, który można przypisać na wskaźnik natywny.  
  
### <a name="remarks"></a>Uwagi  
 A **pin_ptr** stanowi nadzbiór funkcji wskaźnik natywny. W związku z tym, wszystkie elementy, które mogą być przypisane do wskaźnik natywny można również przypisać do **pin_ptr**. Wskaźnika wewnętrznego może wykonać ten sam zestaw operacji co natywnymi wskaźnikami, w tym porównania i arytmetyka wskaźnika.  
  
 Obiekt lub obiekt podrzędny klasy zarządzanej można przypiąć, w którym to przypadku środowiska uruchomieniowego języka wspólnego nie przeniesie go podczas wyrzucania elementów bezużytecznych. Użycie podmiotu zabezpieczeń jest przekazać wskaźnik do danych zarządzanych jako rzeczywisty parametr wywołania funkcji niezarządzanej. Podczas cyklu zbierania środowisko uruchomieniowe Sprawdź metadane utworzone dla przypiętego wskaźnika i nie zostanie przesunięty w elemencie, który wskazuje.  
  
 Przypinanie obiektu przypięcie jego wartość pola aplikacji; oznacza to, że pola podstawowego lub wartość typu. Jednak pola zadeklarowana przez śledzenie uchwytu (`%`) nie są przypięte.  
  
 Przypinanie podobiekcie definiowane w obiekcie zarządzanych efektem przypięcie całego obiektu.  
  
 Jeśli przypiętego wskaźnika jest przypisywana ponownie, aby wskazywał nową wartość, poprzednie wystąpienie wskazywany przestaje być uważany za przypięty.  
  
 Obiekt jest przypięty tylko podczas **pin_ptr** na nią wskazuje. Obiekt nie jest już przypięty po jego przypiętego wskaźnika wykracza poza zakres lub jest ustawiona na [nullptr](../windows/nullptr-cpp-component-extensions.md). Po **pin_ptr** zbliża się poza zakresem, obiekt, który został przypięty można przenieść w stercie modułu odśmiecania pamięci. Natywnymi wskaźnikami, które nadal wskazują obiekt nie zostanie zaktualizowana i usuwając odwołanie do jednego z nich może zgłosić wyjątek ulegnie nieodwracalnej awarii.  
  
 Jeśli nie unieruchamiania wskaźników wskazują obiekt (wszystkie unieruchamiania wskaźników poszło poza zakresem, zostały przypisane do punktu do innych obiektów lub przypisano [nullptr](../windows/nullptr-cpp-component-extensions.md)), obiekt jest gwarantowane, nie można przypiąć.  
  
 Przypiętego wskaźnika można wskazać do uchwytu odwołania, typem wartości lub uchwyt typ spakowany, składowej typu zarządzanego lub element tablicy zarządzanej. Nie może wskazywać typ odwołania.  
  
 Pobieranie adresu **pin_ptr** że wskazuje na obiekt natywny powoduje niezdefiniowane zachowanie.  
  
 Unieruchamiania wskaźników może zostać zadeklarowany jako zmienne lokalne niestatycznych na stosie.  
  
 Nie można użyć unieruchamiania wskaźników jako:  
  
-   parametry funkcji  
  
-   zwracany typ funkcji  
  
-   składowa klasy typu  
  
-   Typ docelowy rzutowania.  
  
 **pin_ptr** znajduje się w `cli` przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [platformy, domyślna i cli przestrzenie nazw](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).  
  
 Aby uzyskać więcej informacji na temat wskaźników wnętrza zobacz [pomocą interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md).  
  
 Aby uzyskać więcej informacji na temat Unieruchamianie wskaźników, zobacz [jak: numer Pin wskaźników oraz tablic](../windows/how-to-pin-pointers-and-arrays.md) i [instrukcje: deklarowanie przypinanie wskaźników i typów wartości](../windows/how-to-declare-pinning-pointers-and-value-types.md).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/clr`  
  
### <a name="examples"></a>Przykłady  
  
 W poniższym przykładzie użyto **pin_ptr** ograniczenie pozycja pierwszego elementu w tablicy.  
  
```cpp  
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
  
 W poniższym przykładzie pokazano, że wskaźnika wewnętrznego można skonwertować do przypiętego wskaźnika, a następnie aby typ zwracany dla operatora address-of (`&`) jest wskaźnika wewnętrznego, gdy argument znajduje się na zarządzanym stosie.  
  
```cpp  
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
  
 Poniższy przykład pokazuje, że przypiętego wskaźnika mogą być rzutowane na innego typu.  
  
```cpp  
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