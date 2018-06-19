---
title: Obsługa zestawów znaków wielobajtowych (zestawy MBCS) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b0381b570cbf9e900d44ac075876e63b6be14a8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863637"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Obsługa zestawów znaków wielobajtowych (zestawy MBCS)
Zestawy znaków wielobajtowych (zestawy MBCS) są to metoda starszych konieczna Obsługa zestawów znaków, takich jak japoński i chiński, której nie można przedstawić w pojedynczy bajt. Jeśli przeprowadzasz nowych aplikacji należy używać Unicode dla wszystkich łańcuchów tekstowych, z wyjątkiem prawdopodobnie ciągów systemu, które nie są widoczne dla użytkowników końcowych. MBCS to starszych technologia która nie jest zalecane w przypadku nowych wdrożeń.  
  
 Najczęstszą implementacją MBCS jest zestawów znaków dwubajtowych (DBCSs). Visual C++ w ogólne i MFC w szczególności, jest w pełni włączone dla zestawów znaków Dwubajtowych.  
  
 Dla przykładów Zobacz pliki kodu źródłowego MFC.  
  
 Używane na rynkach, na których języków użyć dużych zestawów platformy najlepszym sposobem Unicode jest MBCS. MFC obsługuje MBCS przy użyciu danych internationalizable typy i funkcje wykonawcze języka C. Należy wykonać takie same, w kodzie.  
  
 W obszarze MBCS kodowania znaków w bajtach 1 lub 2. W znaki 2-bajtowych, pierwszy lub bajtu sygnalizuje, że jej i następny bajt interpretowane jako jeden znak. Pierwszy bajt, pochodzi z zakresu kodów zarezerwowane do użytku jako realizacji bajtów. Zakresu bajtów może być bajtów potencjalnych klientów zależy od strony kodowej w użyciu. Na przykład strona kodowa japońskiego 932 używa zakresu 0x81 za pośrednictwem 0x9F realizacji bajtów, ale strona kodowa koreański 949 używa innego zakresu.  
  
 Należy wziąć pod uwagę następujące Twojej MBCS programowania.  
  
 Znaki MBCS w środowisku  
 MBCS znaki nie mogą występować w ciągach znaków, takich jak nazwy plików i katalogów.  
  
 Operacje edytowania  
 Operacje w aplikacjach MBCS edytowania powinny działać na znaków, nie w bajtach. Karetkę powinien dzieli znak, przenieść Strzałka w prawo o jeden znak w prawo i tak dalej. **Usuń** należy usunąć znaku; **Cofnij** powinna ponownie.  
  
 Obsługa ciągu  
 W aplikacji, która używa MBCS Obsługa ciągu stwarza szczególne problemy. Pojedynczy ciąg; mieszane znaków obu szerokości w związku z tym należy pamiętać wyszukać realizacji bajtów.  
  
 Obsługa biblioteki wykonawczej  
 Obsługa biblioteki wykonawczej języka C i MFC MBCS, Unicode i jednobajtowych programowania. Ciągi znaków jednobajtowych są przetwarzane `str` rodziny funkcji środowiska wykonawczego, ciągi MBCS są przetwarzane z odpowiednimi `_mbs` funkcje i ciągi Unicode są przetwarzane z odpowiednimi *wcs* funkcje. Implementacje funkcji elementów członkowskich klasy MFC funkcji przenośne środowiska wykonawczego mapowane okolicznościach prawo do normalnej `str` rodziny funkcji, funkcji MBCS lub funkcje Unicode, zgodnie z opisem w "Przenośność MBCS/Unicode".  
  
 Przenośność MBCS/Unicode  
 Przy użyciu pliku nagłówka Tchar.h, można tworzyć MBCS, Unicode i jednobajtowych aplikacji z tego samego źródła. Tchar.h definiuje makra prefiksem *_tcs* , który mapowania `str`, `_mbs`, lub *wcs* funkcje, zależnie od potrzeb. Aby utworzyć MBCS, zdefiniuj symbol **_MBCS**. Aby utworzyć Unicode, zdefiniuj symbol **_unicode —**. Domyślnie **_MBCS** jest zdefiniowany dla aplikacji MFC. Aby uzyskać więcej informacji, zobacz [mapowania zwykłego tekstu w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
> [!NOTE]
>  Zachowanie zdefiniowano zarówno w przypadku definiowania **_unicode —** i **_MBCS**.  
  
 Pliki nagłówkowe Mbctype.h i Mbstring.h zdefiniuj MBCS specyficzne funkcje i makra, które mogą wymagać w niektórych przypadkach. Na przykład `_ismbblead` informuje, czy określone bajtów w ciąg jest bajtu.  
  
 Dla międzynarodowych przenośność kodu programu z [Unicode](../text/support-for-unicode.md) lub zestawy znaków wielobajtowych (zestawy MBCS).  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Włącz MBCS w programach](../text/international-enabling.md)  
  
-   [Włącz zarówno Unicode i MBCS w programach](../text/internationalization-strategies.md)  
  
-   [Umożliwia utworzenie programu międzynarodowych MBCS](../text/mbcs-programming-tips.md)  
  
-   [Widoczne jest podsumowanie programowania MBCS](../text/mbcs-programming-tips.md)  
  
-   [Więcej informacji na temat mapowania zwykłego tekstu przenośności szerokość bajtów](../text/generic-text-mappings-in-tchar-h.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)   
 [Obsługa MBCS w programie Visual C++](../text/mbcs-support-in-visual-cpp.md)