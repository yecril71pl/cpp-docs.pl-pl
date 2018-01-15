---
title: init_seg | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69036ffba2143d166c9ac5c55a5b3ec9008b75bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="initseg"></a>init_seg
**Określonego języka C++**  
  
 Określa słowo kluczowe lub kod sekcję, która wpływa na kolejność, w których uruchamiania wykonywany jest kod.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )  
```  
  
## <a name="remarks"></a>Uwagi  
 Znaczenie terminów *segmentu* i *sekcji* są wymienne, w tym temacie.  
  
 Ponieważ Inicjowanie statyczne obiektów globalnych może obejmować wykonywanie kodu, musisz określić słowa kluczowego, który definiuje kiedy obiekty mają być skonstruowany. Jest to szczególnie ważne użyć **init_seg** pragma w bibliotek dołączanych dynamicznie (dll) lub wymagających inicjowania biblioteki.  
  
 Opcje **init_seg** pragma są:  
  
 **kompilatora**  
 Zarezerwowane do inicjowania biblioteki wykonawczej języka Microsoft C. Obiekty w tej grupie są najpierw wykonane.  
  
 **lib**  
 Dostępny do inicjalizacji dostawców biblioteki klas innych firm. Obiekty w tej grupie są wykonane po oznaczona jako **kompilatora** , ale przed innych.  
  
 **użytkownika**  
 Dostępny dla każdego użytkownika. Obiekty w tej grupie są ostatnio wykonane.  
  
 *Nazwa sekcji*  
 Umożliwia jawnej specyfikacji sekcji inicjowania. Obiekty w określonych przez użytkownika *nazwę sekcji* nie są niejawnie skonstruować; jednak ich adresy są umieszczane w sekcji o nazwie *nazwę sekcji*.  
  
 Nazwa sekcji przekażesz będzie zawierać wskaźniki do funkcji pomocniczych, które utworzy obiektów globalnych zadeklarowany w module po pragma.  
  
 Aby uzyskać listę nazw nie należy używać podczas tworzenia sekcji, zobacz [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 *FUNC — nazwa*  
 Określa funkcję, która ma być wywoływana zamiast `atexit` po zamknięciu programu. Tej funkcji pomocnika wymaga także [atexit —](../c-runtime-library/reference/atexit.md) za pomocą wskaźnika do destruktora dla obiekt globalny. Jeśli określisz identyfikator funkcji pragma w postaci  
  
```  
int __cdecl myexit (void (__cdecl *pf)(void))  
```  
  
 następnie zostanie wywołana funkcja zamiast biblioteki wykonawczej języka C `atexit`. Dzięki temu można utworzyć listę destruktory, wymagające wywoływana, gdy wszystko będzie gotowe do zniszczenia obiektów.  
  
 Jeśli potrzebujesz odroczenie inicjowania (na przykład w bibliotece DLL) można jawnie określić nazwę sekcji. Następnie należy wywołać konstruktorów dla każdego obiektu statycznego.  
  
 Nie ma żadnych stawiać cudzysłów wokół identyfikator `atexit` zastąpienia.  
  
 Obiekty nadal zostaną umieszczone w sekcjach zdefiniowane przez inne pragm XXX_seg.  
  
 Obiekty, które są zadeklarowane w module nie zostaną automatycznie zainicjowane przez C-run-time. Należy do tego użytkownika.  
  
 Domyślnie `init_seg` sekcje są tylko do odczytu. Jeśli nazwa sekcji. CRT, kompilator dyskretnie zmieni atrybutu tylko do odczytu, nawet jeśli jest oznaczony jako do odczytu, zapisu.  
  
 Nie można określić **init_seg** więcej niż raz w jednostce tłumaczenia.  
  
 Nawet jeśli obiektu nie ma zdefiniowanych przez użytkownika konstruktora, konstruktora nie jest jawnie zdefiniowany w kodzie, kompilator może wygenerować (na przykład można powiązać wskaźniki v-table).  W związku z tym kodzie należy wywołać konstruktora generowane przez kompilator.  
  
## <a name="example"></a>Przykład  
  
```  
// pragma_directive_init_seg.cpp  
#include <stdio.h>  
#pragma warning(disable : 4075)  
  
typedef void (__cdecl *PF)(void);  
int cxpf = 0;   // number of destructors we need to call  
PF pfx[200];    // pointers to destructors.  
  
int myexit (PF pf) {  
   pfx[cxpf++] = pf;  
   return 0;  
}  
  
struct A {  
   A() { puts("A()"); }  
   ~A() { puts("~A()"); }  
};  
  
// ctor & dtor called by CRT startup code   
// because this is before the pragma init_seg  
A aaaa;   
  
// The order here is important.  
// Section names must be 8 characters or less.  
// The sections with the same name before the $  
// are merged into one section. The order that  
// they are merged is determined by sorting  
// the characters after the $.  
// InitSegStart and InitSegEnd are used to set  
// boundaries so we can find the real functions  
// that we need to call for initialization.  
  
#pragma section(".mine$a", read)  
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;  
  
#pragma section(".mine$z",read)  
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;  
  
// The comparison for 0 is important.  
// For now, each section is 256 bytes. When they  
// are merged, they are padded with zeros. You  
// can't depend on the section being 256 bytes, but  
// you can depend on it being padded with zeros.  
  
void InitializeObjects () {  
   const PF *x = &InitSegStart;  
   for (++x ; x < &InitSegEnd ; ++x)  
      if (*x) (*x)();  
}  
  
void DestroyObjects () {  
   while (cxpf>0) {  
      --cxpf;  
      (pfx[cxpf])();  
   }  
}  
  
// by default, goes into a read only section  
#pragma init_seg(".mine$m", myexit)  
  
A bbbb;   
A cccc;  
  
int main () {  
   InitializeObjects();  
   DestroyObjects();  
}  
```  
  
```Output  
A()  
A()  
A()  
~A()  
~A()  
~A()  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)