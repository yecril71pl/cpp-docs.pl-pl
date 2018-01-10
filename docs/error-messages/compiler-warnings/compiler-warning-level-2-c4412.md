---
title: "Kompilatora (poziom 2) ostrzeżenie C4412 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4412
dev_langs: C++
helpviewer_keywords: C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92898b9c8e8845ecc8bc650b80cf41a33b3a59d9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4412"></a>Kompilator C4412 ostrzegawcze (poziom 2)
"Funkcja": sygnatura funkcji zawiera typ 'type'; Obiektami C++ są bezpieczne między czystym kodzie i mieszanego lub macierzystego.  
  
 **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015.  
  
 Kompilator wykryto potencjalnie niebezpiecznych sytuacji, co może spowodować błąd środowiska uruchomieniowego: wywołanie jest wykonywane z **/CLR: pure** compiland do funkcji, która została zaimportowana za pośrednictwem dllimport i sygnatura funkcji zawiera niezabezpieczonego typu . Typ jest niebezpieczne, jeśli zawiera funkcji członkowskiej lub ma elementu członkowskiego danych, który jest typem niezabezpieczony lub pośredni do niezabezpieczonego typu.  
  
 To jest niebezpieczne z powodu różnicy w domyślnym wywoływanie Konwencji między kod czysty i natywnego (lub mieszane natywnego i zarządzanego). Podczas importowania (za pośrednictwem `dllimport`) funkcja do **/CLR: pure** compiland, upewnij się, że deklaracje każdego typu w sygnaturze są takie same jak te w compiland, które eksportuje funkcję (ostrożność szczególnie różnice w konwencji wywoływania niejawne).  
  
 Funkcja wirtualny element członkowski jest szczególnie podatne na dać nieoczekiwane wyniki.  Jednak aby mieć pewność, że poprawnych wyników należy przetestować niewirtualną funkcji. Jeśli masz pewność, że w przypadku uzyskiwania poprawnych wyników, możesz zignorować to ostrzeżenie.  
  
 Aby uzyskać więcej informacji na **/CLR: czysty**, zobacz [porady: Migracja do/CLR: pure (C + +/ interfejsu wiersza polecenia)](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md).  
  
 C4412 jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) i [dllexport i dllimport](../../cpp/dllexport-dllimport.md) Aby uzyskać więcej informacji.  
  
 Aby usunąć to ostrzeżenie, Usuń wszystkie funkcje związane z typem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4412.  
  
```  
// C4412.cpp  
// compile with: /c /W2 /clr:pure  
#pragma warning (default : 4412)  
  
struct Unsafe {  
   virtual void __cdecl Test();  
};  
  
struct Safe {  
   int i;  
};  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   Unsafe *pUnsafe = func();   // C4412  
   // pUnsafe->Test();  
  
   Safe *pSafe = func2();   // OK  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest plik nagłówka, który deklaruje dwa typy. `Unsafe` Typu jest niebezpieczne, ponieważ ma ona funkcją członkowską.  
  
```  
// C4412.h  
struct Unsafe {  
   // will be __clrcall if #included in pure compilation  
   // defaults to __cdecl in native or mixed mode compilation  
   virtual void Test(int * pi);  
  
   // try the following line instead  
   // virtual void __cdecl Test(int * pi);  
};  
  
struct Safe {  
   int i;  
};  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie eksportuje funkcji z typów zdefiniowanych w pliku nagłówka.  
  
```  
// C4412_2.cpp  
// compile with: /LD  
#include "C4412.h"  
  
void Unsafe::Test(int * pi) {  
   *pi++;  
}  
  
__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }  
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }  
```  
  
## <a name="example"></a>Przykład  
 Domyślną konwencję wywoływania **/CLR: pure** kompilacji różni się od kodu natywnego.  Gdy wchodzi C4412.h `Test` domyślnie `__clrcall`. Jeśli skompilować i uruchomić ten program (nie należy używać **/c**), program spowoduje zgłoszenie wyjątku.  
  
 Poniższy przykład generuje C4412.  
  
```  
// C4412_3.cpp  
// compile with: /W2 /clr:pure /c /link C4412_2.lib  
#pragma warning (default : 4412)  
#include "C4412.h"  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   int n = 7;  
   Unsafe *pUnsafe = func();   // C4412  
   pUnsafe->Test(&n);  
  
   Safe *pSafe = func2();   // OK  
}  
```