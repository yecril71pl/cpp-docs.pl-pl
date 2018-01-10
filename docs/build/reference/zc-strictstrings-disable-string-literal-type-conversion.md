---
title: "-Zc-: strictStrings (Wyłączanie konwersji typów literału ciągu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Zc:strictStrings
- strictStrings
dev_langs: C++
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f316c5fc9209f968219d770a15e6576880b69954
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (Wyłączanie konwersji typów literału ciągu)
W przypadku kompilator wymaga strict `const`— zgodność kwalifikacji dla wskaźników zainicjowany przy użyciu literałów ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Zc:strictStrings[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli **/Zc: strictstrings** określono kompilator wymusza standardu C++ `const` kwalifikacji literałów ciągów jako typ "tablicę `const char`" lub "tablicę `const wchar_t`", w zależności od deklaracji. Literały ciągu są niezmienne i zmodyfikować zawartość jednej powoduje błąd naruszenia zasad dostępu w czasie wykonywania. Należy zadeklarować wskaźnika ciągu jako `const` Zainicjuj go za pomocą literału ciągu lub użyj jawnej `const_cast` zainicjować niż`const` wskaźnika. Domyślnie lub jeśli **/Zc:strictStrings-** określono kompilator nie Wymuszaj standard C++ `const` kwalifikacje dla wskaźników ciąg zainicjowany przy użyciu literałów ciągów.  
  
 Użyj **/Zc: strictstrings** opcję, aby uniemożliwić kompilacji niepoprawny kod. Ten przykład przedstawia, jak błąd proste deklaracji prowadzi do awarii w czasie wykonywania:  
  
```cpp  
// strictStrings_off.cpp  
// compile by using: cl /W4 strictStrings_off.cpp  
int main() {  
   wchar_t* str = L"hello";  
   str[2] = L'a'; // run-time error: access violation  
}  
```  
  
 Gdy **/Zc: strictstrings** jest włączone, ten sam kod zgłasza błąd w deklaracji `str`.  
  
```cpp  
// strictStrings_on.cpp  
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp  
int main() {  
   wchar_t* str = L"hello"; // error: Conversion from string literal   
   // loses const qualifier  
   str[2] = L'a';   
}  
```  
  
 Jeśli używasz `auto` zadeklarować wskaźnika ciągu, kompilator tworzy poprawny `const` deklaracji typu wskaźnik dla Ciebie. Podjęto próbę zmodyfikowania zawartości `const` wskaźnik został zgłoszony przez kompilatora jako błąd.  
  
> [!NOTE]
>  Standardowa biblioteka C++ w [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] nie obsługuje **/Zc: strictstrings** kompilacje — opcja kompilatora podczas debugowania. Jeśli widzisz kilka [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) output błędy w kompilacji, może to być przyczyną.  
  
 Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić `/Zc:strictStrings` , a następnie wybierz **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [/Zc (zgodność)](../../build/reference/zc-conformance.md)