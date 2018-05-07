---
title: Kompilatora (poziom 1) ostrzeżenie C4691 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4691
dev_langs:
- C++
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9dccce2468c83dd7d14596c1c26e19bd13ad1a70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4691"></a>Kompilator C4691 ostrzegawcze (poziom 1)
'type': oczekiwano typu odwołania w zestawie nieużywane 'Plik' typu zdefiniowanego w bieżącej jednostce tłumaczenia, zamiast tego użyć  
  
 Brak odwołania do pliku metadane zawierające oryginalnej definicji typu, a kompilator jest przy użyciu definicji typu lokalnego.  
  
 W przypadku, gdy są odbudowywania *pliku*, może być ignorowane lub wyłączona z pragma C4691 [ostrzeżenie](../../preprocessor/warning.md).  Oznacza to, że plik, który tworzysz jest taka sama jak pliku, w którym kompilator oczekuje można znaleźć definicji typu, możesz zignorować C4691.  
  
 Jednak nieoczekiwane zachowanie może wystąpić, jeśli kompilator używa definicji, który nie pochodzi z tego samego zestawu, który odwołuje się do metadanych; Typy CLR są wpisywane nie tylko nazwę typu, ale również przez zestaw.  Typ Z z z.dll zestawu jest inny niż typ Z z y.dll zestawu.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera oryginalnej definicji typu.  
  
```  
// C4691_a.cpp  
// compile with: /clr /LD /W1  
public ref class Original_Type {};  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie odwołuje się do C4691_a.dll i deklaruje pola typu Original_Type.  
  
```  
// C4691_b.cpp  
// compile with: /clr /LD  
#using "C4691_a.dll"  
public ref class Client {  
public:  
   Original_Type^ ot;  
};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4691.  Zwróć uwagę, w tym przykładzie zawiera definicję dla Original_Type i nie odwołuje się C4691a.dll.  
  
 Aby rozwiązać, odwołanie do pliku metadanych, który zawiera oryginalnej definicji typu, a następnie usuń lokalnej deklaracji i definicji.  
  
```  
// C4691_c.cpp  
// compile with: /clr /LD /W1  
// C4691 expected  
  
// Uncomment the following line to resolve.  
// #using "C4691_a.dll"  
#using "C4691_b.dll"  
  
// Delete the following line to resolve.  
ref class Original_Type;  
  
public ref class MyClass : Client {};  
```