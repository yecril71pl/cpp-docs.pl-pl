---
title: Konstruktory kopiujące i kopiujące operatory przypisania (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1292240e5343c461142e8c6029c277175f6a62f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417265"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Konstruktory kopiujące i kopiujące operatory przypisania (C++)
> [!NOTE]
>  Począwszy od języka C ++ 11 dwa rodzaje przypisania są obsługiwane w języku: *skopiuj przypisania* i *Przenieś przypisania*. W tym artykule "przydziału" oznacza przypisania kopiowania, chyba że jawnie inaczej. Informacje o przypisywaniu przenoszenia, zobacz [konstruktory przenoszenia i operatory przypisania przenoszenia (C++)](http://msdn.microsoft.com/en-us/1442de5f-37a5-42a1-83a6-ec9cfe0414db).  
>   
>  Operacja przypisania i z operacji inicjowania spowodować obiektów do skopiowania.  
  
-   **Przypisanie**: gdy wartość jeden obiekt jest przypisany do innego obiektu, pierwszy obiekt jest kopiowany do drugiego obiektu. W związku z tym  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     powoduje, że wartość `b` ma zostać skopiowany na `a`.  
  
-   **Inicjowanie**: inicjowanie występuje po zadeklarowaniu nowego obiektu, gdy argumenty są przekazywane do funkcji według wartości lub wartości są zwracane z funkcji przez wartość.  
  
 Można zdefiniować semantykę "Kopiuj" dla obiektów typu klasy. Na przykład, rozważmy ten kod:  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 Poprzedni kod może oznaczać "skopiuj zawartość FILE1. DAT, aby Plik2. DAT"lub może oznaczać"plik2 zignorować. DAT i `b` drugi dojścia do FILE1.DAT. " Odpowiednie semantyki kopiowanie należy dołączyć do każdej klasy, w następujący sposób.  
  
-   Za pomocą operatora przypisania `operator=` wraz z odwołaniem do typu klasy jako zwracany typ i parametr, który jest przekazywana przez `const` odwołania — na przykład `ClassName& operator=(const ClassName& x);`.  
  
-   Za pomocą konstruktora kopiującego.   
  
 Jeśli nie zadeklarować konstruktora kopiującego, kompilator generuje konstruktora kopiującego member-wise dla Ciebie.  Jeśli nie można zadeklarować operatora przypisania kopii, kompilator generuje operatora przypisania kopii member-wise dla Ciebie. Deklarowanie konstruktora kopiującego odrzuca operatora przypisania kopii generowane przez kompilator, ani na odwrót. W przypadku zastosowania jednej, zalecamy również stosowanie innego tak, aby znaczenie kodu jest wyczyszczone.  
   
 Konstruktor kopiujący przyjmuje argument typu * klasy — nazwa ***&**, gdzie *Nazwa klasy* jest nazwa klasy, dla którego zdefiniowano konstruktora. Na przykład:  
  
```cpp  
// spec1_copying_class_objects.cpp  
class Window  
{  
public:  
    Window( const Window& ); // Declare copy constructor.  
    // ...  
};  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  Typ argumentu konstruktora kopiującego *const klasy — Nazwa *** &** Jeśli to możliwe. Zapobiega to przypadkowym zmianom obiektu, z którego jest kopiowanie konstruktora kopiującego. Umożliwia również kopiowanie z **const** obiektów.  
  
## <a name="compiler-generated-copy-constructors"></a>Wygenerowanego przez kompilator kopiowanie konstruktorów  
 Kopiowanie generowane przez kompilator konstruktorów, takich jak konstruktorów zdefiniowanych przez użytkownika kopiowania mieć jeden argument typu "odwołanie do *Nazwa klasy*." Jest wyjątek, jeśli wszystkie klasy podstawowe i element członkowski klasy kopiowanie konstruktorów zadeklarowany jako jeden argument typu biorąc **const** * klasy — nazwa ***&**. W takim przypadku argument konstruktora kopiowania generowane przez kompilator jest również **const**.  
  
 Jeśli typ argumentu do konstruktora kopiowania nie jest **const**, inicjowanie przez skopiowanie **const** obiektu generuje błąd. Sytuacja odwrotna nie jest prawdziwe: Jeśli wartością argumentu jest **const**, można zainicjować przez skopiowanie obiektu, który nie jest **const**.  
  
 Operatory przypisania generowane przez kompilator wykonują te same czynności w odniesieniu do **const.** Podejmują jeden argument typu *klasy — Nazwa *** &** o ile operatory przypisania w wszystkie klasy podstawowe i element członkowski przyjmują argumentów typu **const** *Nazwa klasy &.* W takim przypadku klasa obiektu generowane ma operatora przypisania **const** argumentu.  
  
> [!NOTE]
>  Jeśli wirtualne klasy podstawowe są inicjowane przez kopiowanie konstruktorów, generowane przez kompilator lub zdefiniowanej przez użytkownika, są one inicjowane tylko raz: w momencie, gdy są one utworzony.  
  
 Konsekwencje są podobne do konstruktora kopiowania. Jeśli typ argumentu nie jest **const**, przypisanie z **const** obiektu generuje błąd. Sytuacja odwrotna nie jest prawdziwe: Jeśli **const** wartość jest przypisywana wartość, która nie jest **const**, przypisanie zakończy się pomyślnie.  
  
 Aby uzyskać więcej informacji na temat przypisania przeciążone operatory zobacz [przypisania](../cpp/assignment.md).  
  
