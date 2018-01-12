---
title: Ograniczenia nazw symboli | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.restrictions.name
dev_langs: C++
helpviewer_keywords:
- symbol names
- symbols, names
- restrictions, symbol names
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d82720142517468fffd4388f000f3830e8edb4ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="symbol-name-restrictions"></a>Ograniczenia dotyczące nazwy symbolu
Ograniczenia dotyczące nazwy symbolu są następujące:  
  
-   Wszystkie [symbole](../windows/symbols-resource-identifiers.md) musi być unikatowa w zakresie aplikacji. Zapobiega to konflikt definicje symbolu w plikach nagłówka.  
  
-   Prawidłowe znaki dla nazwy symbolu to A-Z, a-z, 0-9 i znaki podkreślenia (_).  
  
-   Nazwy symboli nie może rozpoczynać się cyfrą i mogą zawierać maksymalnie 247 znaków.  
  
-   Nazwy symboli nie może zawierać spacji.  
  
-   Nazwy symboli nie jest uwzględniana, ale jest zachowane w przypadku pierwszego definicji symbolu. Plik nagłówka, który definiuje symbole jest używany przez Edytor kompilatora zasobów i programach języka C++ w odwołaniu zasoby zdefiniowane w pliku zasobu. Dla dwóch nazw symboli który różnić tylko w przypadku, program w języku C++ zostanie wyświetlony dwa oddzielne symbole podczas kompilatora/Edytor zasobów zobaczą obie nazwy jako odnoszące się do jednego pojedynczego symbolu.  
  
    > [!NOTE]
    >  Jeśli nie wykonuj schemat nazwę standardowego symbolu (ID*_[keyword]) opisane poniżej, a nazwę symbolu stanie się być takie same jak słowa kluczowego znane kompilator skryptu zasobu w trakcie tworzenia pliku skryptu zasobu spowoduje pozornie losowe błędu Generowanie, który jest trudne do diagnozowania. Aby tego uniknąć, należy stosować się do standardowego schemat nazewnictwa.  
  
 Nazwy symboli ma opisową prefiksy, wskazujące rodzaj zasobu lub obiekt, który reprezentuje. Tymi prefiksami opisową zaczynać się od identyfikatora kombinacja tekstu Biblioteka Microsoft Foundation Class (MFC) używa konwencji nazewnictwa symbol pokazano w poniższej tabeli.  
  
|Kategoria|Prefiks|Zastosowanie|  
|--------------|------------|---------|  
|Resources|IDR_ IDD_ IDC_ IDI_ IDB_|Akceleratora lub menu (i skojarzone lub niestandardowych zasobów) — okno dialogowe mapy bitowej ikona kursora|  
|Elementy menu|ID_|Element menu|  
|Polecenia|ID_|Polecenie|  
|Formanty i okno podrzędne|IDC_|Formant|  
|Ciągi|IDS_|Ciąg w tabeli ciągów|  
|MFC|AFX_|Zarezerwowane dla wstępnie zdefiniowane symbole MFC|  
  

  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiana symbolu lub nazwy symbolu (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)   
 [Ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md)   
 [Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)