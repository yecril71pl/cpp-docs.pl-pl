---
title: Style przycisków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BS_DEFPUSHBUTTON
- BS_NOTIFY
- BS_MULTILINE
- BS_AUTOCHECKBOX
- BS_3STATE
- BS_BITMAP
- BS_TOP
- BS_PUSHBUTTON
- BS_PUSHLIKE
- BS_AUTO3STATE
- BS_CHECKBOX
- BS_AUTORADIOBUTTON
- BS_RADIOBUTTON
- BS_OWNERDRAW
- BS_LEFT
- BS_USERBUTTON
- BS_RIGHTBUTTON
- BS_RIGHT
- BS_LEFTTEXT
- BS_TEXT
- BS_BOTTOM
- BS_GROUPBOX
- BS_FLAT
- BS_VCENTER
- BS_ICON
- BS_CENTER
dev_langs:
- C++
helpviewer_keywords:
- BS_NOTIFY constant [MFC]
- BS_RIGHTBUTTON constant [MFC]
- styles [MFC], button objects
- BS_USERBUTTON constant [MFC]
- BS_VCENTER constant [MFC]
- BS_PUSHLIKE constant [MFC]
- BS_RADIOBUTTON constant [MFC]
- BS_PUSHBUTTON constant [MFC]
- BS_DEFPUSHBUTTON constant [MFC]
- BS_LEFTTEXT constant [MFC]
- button objects (CButton), button styles
- BS_AUTO3STATE constant [MFC]
- BS_3STATE constant [MFC]
- BS_OWNERDRAW constant [MFC]
- BS_AUTORADIOBUTTON constant [MFC]
- BS_GROUPBOX constant [MFC]
- BS_BITMAP constant [MFC]
- BS_CENTER constant [MFC]
- BS_MULTILINE constant [MFC]
- BS_BOTTOM constant [MFC]
- BS_FLAT constant [MFC]
- BS_AUTOCHECKBOX constant [MFC]
- BS_RIGHT constant [MFC]
- BS_CHECKBOX constant [MFC]
- BS_LEFT constant [MFC]
- BS_ICON constant [MFC]
- BS_TOP constant [MFC]
- BS_TEXT constant
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ec945c95b81570e52cca03ed4e52355350d8121
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="button-styles"></a>Style przycisku
W tym temacie opisano typy przycisk i style.  
  
## <a name="button-types"></a>Przycisk typów  
 Poniższa tabela zawiera listę typów przycisku. Opcjonalnie można wybrać jedną z następujących czynności. Jeśli nie określisz typ przycisku, wartością domyślną jest `BS_PUSHBUTTON`.  
  
|Typ|Opis|  
|----------|-----------------|  
|`BS_3STATE`|Tworzy przycisk pola wyboru z trzech stanów: `BST_CHECKED`, `BST_INDETERMINATE`, i `BST_UNCHECKED`. Kliknięcie przycisku wysyła `BN_CLICKED` powiadomień do okna nadrzędnego, ale nie ulega zmianie stanu przycisku. Domyślnie tekstu jest wyświetlana z prawej strony pola wyboru. Aby wyświetlić tekst pola wyboru po lewej, użyj `BS_LEFTTEXT` lub `BS_RIGHTBUTTON` styl.|  
|`BS_AUTO3STATE`|Tworzy przycisk pola wyboru z trzech stanów: `BST_CHECKED`, `BST_INDETERMINATE`, i `BST_UNCHECKED`. Kliknięcie przycisku wysyła `BN_CLICKED` powiadomień do okna nadrzędnego i zmienia stan przycisku. Przycisk stany cykl w celu `BST_CHECKED`, `BST_INDETERMINATE`, i `BST_UNCHECKED`. Domyślnie tekstu jest wyświetlana z prawej strony pola wyboru. Aby wyświetlić tekst pola wyboru po lewej, użyj `BS_LEFTTEXT` lub `BS_RIGHTBUTTON` styl.|  
|`BS_AUTOCHECKBOX`|Tworzy przycisk pola wyboru z dwoma stanami: `BST_CHECKED` i `BST_UNCHECKED`. Kliknięcie przycisku wysyła `BN_CLICKED` powiadomień do okna nadrzędnego i zmienia stan przycisku. Domyślnie tekstu jest wyświetlana z prawej strony pola wyboru. Aby wyświetlić tekst pola wyboru po lewej, użyj `BS_LEFTTEXT` lub `BS_RIGHTBUTTON` styl.|  
|`BS_AUTORADIOBUTTON`|Tworzy przycisk radiowy z dwoma stanami: `BST_CHECKED` i `BST_UNCHECKED`. Przyciski radiowe są zazwyczaj używane w grupy z każdą grupą o najwyżej jedną opcję zaznaczone naraz. Kliknięcie przycisku wysyła `BN_CLICKED` powiadomień do okna nadrzędnego, ustawia stan przycisku radiowego klikniętej `BST_CHECKED`i ustawia stany innych przycisków radiowych w grupie przycisków do `BST_UNCHECKED`. Domyślnie tekst jest wyświetlany po prawej stronie przycisku radiowego. Aby wyświetlić tekst do lewego przycisku radiowego, użyj `BS_LEFTTEXT` lub `BS_RIGHTBUTTON` styl.|  
|`BS_CHECKBOX`|Tworzy przycisk pola wyboru z dwoma stanami: `BST_CHECKED` i `BST_UNCHECKED`. Kliknięcie przycisku wysyła `BN_CLICKED` powiadomień do okna nadrzędnego, ale nie ulega zmianie stanu przycisku. Domyślnie tekstu jest wyświetlana z prawej strony pola wyboru. Aby wyświetlić tekst pola wyboru po lewej, użyj `BS_LEFTTEXT` lub `BS_RIGHTBUTTON` styl.|  
|`BS_COMMANDLINK`|Tworzy łącze przycisku. Przycisk polecenia łącze jest specyficzne dla przycisku polecenia [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] wyświetlający zieloną strzałkę w lewo głównego tekstu i Uwaga poniżej tekstu głównego. Można ustawić przy użyciu tekstu Uwaga [CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote).|  
|`BS_DEFCOMMANDLINK`|Tworzy łącze przycisku. Przycisk polecenia łącze jest specyficzne dla przycisku polecenia [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] wyświetlający zieloną strzałkę w lewo głównego tekstu i Uwaga poniżej tekstu głównego. Można ustawić przy użyciu tekstu Uwaga [CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote). Jeśli przycisk jest w oknie dialogowym, naciskając klawisz ENTER klucza wysyła `BN_CLICKED` powiadomień do okna dialogowego, nawet wtedy, gdy przycisk ma fokus wprowadzania.|  
|`BS_DEFPUSHBUTTON`|Tworzy przycisku polecenia, który ma duże czarnym obramowaniem. Jeśli przycisk jest w oknie dialogowym, naciskając klawisz ENTER klucza wysyła `BN_CLICKED` powiadomień do okna dialogowego, nawet wtedy, gdy przycisk ma fokus wprowadzania.|  
|`BS_DEFSPLITBUTTON`|Tworzy przycisk podziału. Przycisk pokrętła jest specyficzne dla przycisku polecenia [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] zawierający strzałkę listy rozwijanej obok przycisku. Po kliknięciu przycisku polecenia domyślny jest wykonywany. Gdy kliknij strzałkę listy rozwijanej, zostanie wyświetlone menu dodatkowych poleceń. Jeśli w oknie dialogowym przycisk podziału, naciskając klawisz ENTER klucza wysyła `BN_CLICKED` powiadomień do okna dialogowego, nawet wtedy, gdy przycisk ma fokus wprowadzania|  
|`BS_GROUPBOX`|Tworzy prostokąt, w którym można grupować innych przycisków. Tekst skojarzony z tym stylem jest wyświetlany w prawym górnym rogu prostokąta.|  
|`BS_OWNERDRAW`|Tworzy przycisk rysowanych przez właściciela. Wywołania framework `DrawItem` metodą podczas visual aspekt przycisku został zmieniony. Można ustawić ten styl, korzystając z `CBitmapButton` klasy.|  
|`BS_PUSHBUTTON`|Tworzy przycisku polecenia, który wysyła `BN_CLICKED` powiadomień do okna nadrzędnego, gdy użytkownik kliknie przycisk.|  
|`BS_RADIOBUTTON`|Tworzy przycisk radiowy z dwoma stanami: `BST_CHECKED` i `BST_UNCHECKED`. Przyciski radiowe są zazwyczaj używane w grupy z każdą grupą o najwyżej jedną opcję zaznaczone naraz. Kliknięcie przycisku wysyła `BN_CLICKED` powiadomień do okna nadrzędnego, ale nie zmienia się automatycznie stan dowolnego przycisku w grupie. Domyślnie tekst jest wyświetlany po prawej stronie przycisku radiowego. Aby wyświetlić tekst do lewego przycisku radiowego, użyj `BS_LEFTTEXT` lub `BS_RIGHTBUTTON` styl.|  
|`BS_SPLITBUTTON`|Tworzy przycisk podziału. Przycisk pokrętła jest specyficzne dla przycisku polecenia [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] zawierający strzałkę listy rozwijanej obok przycisku. Po kliknięciu przycisku polecenia domyślny jest wykonywany. Gdy kliknij strzałkę listy rozwijanej, zostanie wyświetlone menu dodatkowych poleceń.|  
|`BS_USERBUTTON`|Przestarzałe, ale podany w celu zapewnienia zgodności z 16-bitowych wersjach systemu Windows. Należy użyć aplikacji Win32 `BS_OWNERDRAW` zamiast tego.|  
  
## <a name="radio-button-and-check-box-styles"></a>Przycisk radiowy i style pola wyboru  
 W poniższej tabeli wymieniono style, które są specyficzne dla przycisków radiowych i pól wyboru. Te style są ignorowane w innych typach przycisku. Opcjonalnie można wybrać co najmniej jeden z następujących czynności.  
  
|Styl|Opis|  
|-----------|-----------------|  
|`BS_LEFTTEXT`|W połączeniu ze stylem pole wyboru lub przycisku radiowego, tekst, który pojawia się po lewej stronie pola wyboru lub przycisku radiowego.|  
|`BS_RIGHTBUTTON`|W połączeniu ze stylem pole wyboru lub przycisku radiowego, tekst, który pojawia się po lewej stronie pola wyboru lub przycisku radiowego. Ten styl jest taki sam jak `BS_LEFTTEXT` stylu.|  
|`BS_PUSHLIKE`|Powoduje, że pole wyboru lub przycisku radiowego wyglądu i zachowania jak przycisk polecenia. Przycisk jest wciśnięty, gdy jego stan jest `BST_CHECKED`, naciśnięciu i gdy jego stan jest niedostępne `BST_INDETERMINATE`oraz zwalniać przy jej stan to `BST_UNCHECKED`.|  
  
## <a name="text-alignment-styles"></a>Style wyrównanie tekstu  
 W poniższej tabeli wymieniono opcje wyrównania tekstu w poziomie i w pionie. Opcjonalnie można wybrać jedną z następujących czynności.  
  
|Styl|Opis|  
|-----------|-----------------|  
|`BS_LEFT`|Po lewej Wyrównanie tekstu w prostokącie przycisku. Jednak jeśli przycisku ma postać pola wyboru lub przycisku radiowego, który nie ma `BS_RIGHTBUTTON` stylu, pozostanie tekst wyrównany do prawej strony pola wyboru lub przycisku radiowego.|  
|`BS_RIGHT`|Prawo wyrównanie tekstu w prostokącie przycisku. Jednak jeśli przycisku ma postać pola wyboru lub przycisku radiowego, który nie ma `BS_RIGHTBUTTON` styl, tekst wyrównany do prawej strony pola wyboru lub przycisku radiowego jest odpowiednia.|  
|`BS_CENTER`|Wyśrodkowuje tekst w poziomie w prostokącie przycisku.|  
|`BS_TOP`|Umieszcza tekst w górnej krawędzi prostokąta przycisku.|  
|`BS_BOTTOM`|Umieszcza tekst u dołu prostokąt przycisku.|  
|`BS_VCENTER`|W centrach tekstu w prostokącie przycisku.|  
  
## <a name="button-content-options"></a>Przycisk Opcje zawartości  
 W poniższej tabeli wymieniono opcje, które wskazują na to, co jest wyświetlany na przycisku. Przycisk typy, które tylko wyświetlić tekst Ignoruj style. Opcjonalnie można wybrać jedną z następujących czynności.  
  
|Styl|Opis|  
|-----------|-----------------|  
|`BS_BITMAP`|Określa, że przycisk wyświetla mapy bitowej.|  
|`BS_ICON`|Określa, czy przycisk wyświetla ikonę.|  
|`BS_TEXT`|Określa, czy przycisk jest wyświetlany tekst.|  
  
## <a name="other-options"></a>Inne opcje  
 W poniższej tabeli wymieniono dodatkowe opcje, które można używać z dowolnego typu przycisku. Opcjonalnie można wybrać co najmniej jeden z następujących czynności.  
  
|Styl|Opis|  
|-----------|-----------------|  
|`BS_FLAT`|Określa, czy przycisk jest dwuwymiarowa i nie jest rysowane z cieniowaniem domyślne do utworzenia obrazu trójwymiarowy.|  
|`BS_MULTILINE`|Koduje tekst przycisku, który ma wiele wierszy, jeśli ciąg tekstowy jest za długa, aby zmieścić ją w pojedynczym wierszu w prostokącie przycisku.|  
|`BS_NOTIFY`|Włącza przycisk, aby wysłać `BN_DBLCLK`, `BN_KILLFOCUS`, i `BN_SETFOCUS` komunikatów powiadomień do jej okna nadrzędnego. Należy pamiętać, że przyciski wysyłania `BN_CLICKED` powiadomienia niezależnie od tego, czy ten styl jest określony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Style używane przez MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../../mfc/reference/cbutton-class.md#create) [style przycisków](http://msdn.microsoft.com/library/windows/desktop/bb775951)   



