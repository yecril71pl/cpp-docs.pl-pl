---
title: interior_ptr (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a83182151ccb85b920a37713b70df53b383b8919
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879110"
---
# <a name="interiorptr-ccli"></a>interior_ptr (C++/CLI)
*Wskaźnik wewnętrzny* deklaruje wskaźnik do wewnątrz typu odwołania, ale nie samego obiektu. Wskaźnik wewnętrzny może wskazywać dojścia odwołania, typu wartości, dojście do typu opakowanego, elementu członkowskiego typu zarządzanego lub element tablicy zarządzanej.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych.)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do środowiska uruchomieniowego systemu Windows.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 W poniższym przykładzie składni pokazano wskaźnik wewnętrzny.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
cli::interior_ptr<cv_qualifier type> var = &initializer;  
```  
  
### <a name="parameters"></a>Parametry  
 *cv_qualifier*  
 **Const** lub `volatile` kwalifikatorów.  
  
 *Typ*  
 Typ *inicjatora*.  
  
 *var*  
 Nazwa `interior_ptr` zmiennej.  
  
 *initializer*  
 Element członkowski typu referencyjnego, element tablicy zarządzanej lub inny obiekt, który można przypisać do wskaźnika natywnego.  
  
### <a name="remarks"></a>Uwagi  
 Wskaźnik natywny nie jest w stanie śledzenia elementu jako jego zmiany lokalizacji w stercie zarządzanej wyniki z modułu zbierającego elementy bezużyteczne przenoszenie wystąpienia obiektu. Aby wskaźnik do poprawnie odwołuje się do wystąpienia środowiska uruchomieniowego musi zaktualizować wskaźnik do nowo pozycjonowane obiektu.  
  
 `interior_ptr` Reprezentuje podzbiorem funkcji wskaźnik natywny.  W związku z tym wszystkie elementy, które można przypisać na wskaźnik natywny można również przypisać do `interior_ptr`.  Wskaźnik wewnętrzny może wykonać ten sam zestaw operacji jako wskaźników natywnych, w tym porównania i arytmetyka wskaźnika.  
  
 Wskaźnik wewnętrzny mogą być deklarowane tylko na stosie.  Wskaźnik wewnętrzny nie może być zadeklarowany jako element członkowski klasy.  
  
 Ponieważ wewnętrznych wskaźników istnieje tylko na stosie, pobieranie adresu wskaźnik wewnętrzny daje niezarządzanego wskaźnika.  
  
 `interior_ptr` niejawna konwersja na ma `bool`, dzięki czemu do wykorzystania w instrukcji warunkowej.  
  
 Informacje na temat sposobu zadeklarować wskaźnik wewnętrzny wskazującą na obiekt nie może zostać przeniesiona na stercie zbierane pamięci, zobacz [pin_ptr](../windows/pin-ptr-cpp-cli.md).  
  
 `interior_ptr` znajduje się w przestrzeni nazw cli.  Zobacz [platformy, domyślna i cli przestrzenie nazw](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji o wewnętrznych wskaźników zobacz  
  
-   [Instrukcje: deklarowanie wewnętrznych wskaźników i zarządzanych tablic oraz posługiwanie się nimi (C++/CLI)](../windows/how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)  
  
-   [Instrukcje: deklarowanie typów wartości za pomocą słowa kluczowego interior_ptr (C++/CLI)](../windows/how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)  
  
-   [Instrukcje: funkcje przeładowania z wewnętrznymi i natywnymi wskaźnikami (C++/CLI)](../windows/how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)  
  
-   [Instrukcje: deklarowanie wewnętrznych wskaźników za pomocą słowa kluczowego const (C++/CLI)](../windows/how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład przedstawia sposób deklarowanie i użycie wskaźnik wewnętrzny do typu referencyjnego.  
  
```cpp  
// interior_ptr.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
public:  
   int data;  
};  
  
int main() {  
   MyClass ^ h_MyClass = gcnew MyClass;  
   h_MyClass->data = 1;  
   Console::WriteLine(h_MyClass->data);  
  
   interior_ptr<int> p = &(h_MyClass->data);  
   *p = 2;  
   Console::WriteLine(h_MyClass->data);  
  
   // alternatively  
   interior_ptr<MyClass ^> p2 = &h_MyClass;  
   (*p2)->data = 3;  
   Console::WriteLine((*p2)->data);  
}  
```  
  
 **Output**  
  
```Output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)