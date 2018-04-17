---
title: Zestawy znaków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81b1046ea7588a6cc5eb3274473f4e4bee9daccd
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="character-sets"></a>Zestawy znaków
Tekst program w języku C++ są przechowywane w plikach źródłowych, korzystających z kodowania znaków określonego. C++ standard określa zestaw znaków źródła podstawowe dla plików źródłowych i zestaw znaków wykonania podstawowych dla skompilowanych plików. Visual C++ pozwala dodatkowy zestaw znaków specyficzne dla ustawień regionalnych do użycia w plikach źródłowych i skompilowane pliki.  
  
## <a name="character-sets"></a>Zestawy znaków  
 Określa C++ standard *zestaw znaków źródła podstawowe* które mogą być używane w plikach źródłowych. Do reprezentowania znaków spoza tego zestawu, można określić dodatkowe znaki przy użyciu *Uniwersalna nazwa znaku*. Podczas kompilacji, *zestaw znaków wykonania podstawowych* i *zestaw znaków dwubajtowych wykonywania podstawowych* reprezentują znaków i ciągi, które mogą być wyświetlane w programie. Implementacja Visual C++ pozwala dodatkowe znaki w kodzie źródłowym i skompilowanego kodu.  
  
### <a name="basic-source-character-set"></a>Zestaw znaków źródła podstawowe  
 *Zestaw znaków źródła podstawowe* składa się z 96 znaków, które mogą być używane w plikach źródłowych. Ten zestaw zawiera znak spacji, tabulator poziomy, tabulator pionowy, źródła danych formularza i znaki nowego wiersza, a to zestaw znaków graficznych:  
  
 `a b c d e f g h i j k l m n o p q r s t u v w x y z`  
  
 `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`  
  
 `0 1 2 3 4 5 6 7 8 9`  
  
 `_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`  
  
 **Microsoft Specific**  
  
 Visual C++ obejmuje `$` znak jako członek zestaw znaków źródła podstawowych. Visual C++ pozwala dodatkowy zestaw znaków do użycia w plikach źródłowych oparte na kodowanie pliku. Domyślnie program Visual Studio przechowuje pliki źródłowe za pomocą domyślną stronę kodową. Gdy pliki źródłowe zostaną zapisane przy użyciu ustawień regionalnych codepage lub Unicode codepage, Visual C++ umożliwia użycie znaków tę stronę kodową w kodzie źródłowym z wyjątkiem kody kontrolki nie jawnie dozwolone w znak podstawowe źródło zestaw. Na przykład można umieścić japońskie znaki w komentarze, identyfikatory lub literałów ciągów, jeśli zapiszesz plik przy użyciu japońskiego stronę kodową. Visual C++ nie zezwala na sekwencji znaków, których nie można przetłumaczyć prawidłowych znaków wielobajtowych lub kody znaków Unicode. W zależności od opcji kompilatora nie wszystkie dozwolonych znaków mogą występować w identyfikatorach. Aby uzyskać więcej informacji, zobacz [identyfikatory](../cpp/identifiers-cpp.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
### <a name="universal-character-names"></a>Uniwersalne nazwy znaków  
 Ponieważ programy C++ mogą używać wielu więcej znaków niż określone w zestawie znaków źródła podstawowe, te znaki można określić w sposób przenośnych za pomocą *uniwersalne nazwy znaków*. Nazwa zawierająca znaki uniwersalne składa się z sekwencji znaków, które reprezentują punkt kodu Unicode.  Te mieć dwie formy. Użyj `\UNNNNNNNN` reprezentuje punkt kodu Unicode w formularzu U + NNNNNNNN, gdzie NNNNNNNN jest numerem punktu 8 cyfr kodu szesnastkowego. Użyj czterocyfrowe `\uNNNN` reprezentuje punkt kodu Unicode w formularzu U + 0000NNNN.  
  
 Uniwersalne nazwy znaków można w identyfikatorów i literały ciągów i znakowe. Nazwa zawierająca znaki uniwersalne nie może być używana do reprezentowania zastępczego punktu kodu z zakresu od 0xD800 — 0xDFFF. Zamiast tego należy użyć punktu odpowiedni kod; kompilator automatycznie generuje wszelkie wymagane części znaku dwuskładnikowego. Dodatkowe ograniczenia dotyczą uniwersalne nazwy znaków, które mogą być używane w identyfikatorów. Aby uzyskać więcej informacji, zobacz [identyfikatory](../cpp/identifiers-cpp.md) i [literały ciągów i znakowe](../cpp/string-and-character-literals-cpp.md).  
  
 **Microsoft Specific**  
  
 Kompilator Visual C++ zamiennie traktuje znaku w formularzach nazwa zawierająca znaki uniwersalne i literału. Na przykład można zadeklarować identyfikatora za pomocą formularza nazwa zawierająca znaki uniwersalne i używać go w formie literału:  
  
```cpp  
auto \u30AD = 42; // \u30AD is 'キ'  
if (キ == 42) return true; // \u30AD and キ are the same to the compiler  
  
```  
  
 Format znaki rozszerzone do Schowka systemu Windows jest specyficzne dla aplikacji, ustawienia regionalne. Wycinanie i wklejanie te znaki w kodzie z innej aplikacji może powodować kodowania nieoczekiwany znak. Może to spowodować analizowanie błędów nie Przyczyna widoczne w kodzie. Firma Microsoft zaleca ustawienie Twojego źródła kodowanie pliku na stronę kodową Unicode przed wklejeniem znaki rozszerzone. Zalecamy również użyć aplikacji tablicy znaków lub edytorze IME można wygenerować znaki rozszerzone.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
### <a name="basic-execution-character-set"></a>Zestaw znaków wykonania podstawowych  
 *Zestaw znaków wykonania podstawowych* i *zestaw znaków dwubajtowych wykonywania podstawowych* składają się wszystkie znaki w zestawie znaków źródła podstawowe i znaków kontrolnych, które reprezentują alertu, BACKSPACE, znaków powrotu karetki i znakiem pustym.   *Zestaw znaków wykonania* i *zestaw znaków dwubajtowych wykonywania* są nadzbiorami podstawowe zestawy. Obejmują one zdefiniowane w implementacji źródła znaki spoza zestawu znaków podstawowego źródła. Zestaw znaków wykonania ma reprezentację ustawień regionalnych.