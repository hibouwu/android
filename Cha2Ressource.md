# **Chapitre 2 : Les ressources et le format XML**

# **第二章：资源与 XML 格式**

## **1. Introduction aux ressources / 资源简介**

Le répertoire **`res/`** contient toutes les ressources nécessaires à l’application pour s’adapter à différents écrans.  
**`res/` 目录包含应用程序用于适应不同屏幕的所有资源。**  

### 📌 **Pourquoi organiser les ressources ? / 为什么要组织资源？**

- **Éviter la perte de qualité** en proposant plusieurs tailles d’images.  
  **提供多种尺寸的图片，以避免放大后质量下降。**  
- **Faciliter l’adaptation à différentes résolutions et langues.**  
  **确保在不同设备上正确显示内容，并适应不同的语言。**  
- **Android sélectionne automatiquement la bonne ressource** selon le terminal.  
  **Android 会根据设备自动选择适当的资源。**  

---

## **2. Le format XML / XML 格式**

### **📌 XML, un langage de balisage / XML，一种标记语言**

XML est un **langage de balisage** similaire au HTML.  
**XML 是一种类似 HTML 的标记语言，HTML 间接衍生自 XML。**  

📌 **Différences avec un langage de programmation (Java, C++)** :  

| **Langage de programmation** | **Langage de balisage** (XML) |
|-----------------------------|------------------------------|
| Effectue des calculs et affiche des résultats. | Organise et structure des données. |
| Utilisé pour la logique métier. | Utilisé pour stocker des informations de manière structurée. |

Un fichier XML est **interprété** par un programme, tout comme un navigateur web interprète du HTML.  
**XML 文件需要由程序解析，就像浏览器解析 HTML 一样。**

---

## **3. Exemple pratique : Contacts en XML / XML 实例：存储联系人**

Imaginons que nous souhaitons stocker nos contacts en XML.  

```xml
<?xml version="1.0" encoding="utf-8"?>
<contacts>
    <contact>
        <nom>Anaïs</nom>
        <telephone>1111111111</telephone>
    </contact>
    <contact>
        <nom>Romain</nom>
        <telephone>2222222222</telephone>
    </contact>
</contacts>

```
- **&lt;?xml version="1.0" encoding="utf-8"?&gt;** : déclaration XML, On utilise la version 1.0 de XML et l’encodage UTF-8.
- **&lt;contacts&gt;** : la balise, Elle commence par un chevron ouvrant < et se termine par un chevron fermant >.
**il va falloir la fermer** : 
- Soit par la balise fermante **&lt;/contacts&gt;** : vous pourrez avoir du contenu entre la balise ouvrante et la balise fermante.
- Soit on ferme la balise directement dans son corps : **&lt;contact&gt note="20"/&gt;** : on peut ajouter des attributs à la balise, note="20" est une attribut dans cet exemple. équivalent à : **&lt;contact note="20"&gt;&lt;/contact&gt;** qui n'pas d'attribut, mais un contenu.


```xml
<?xml version="1.0" encoding="utf-8"?>
<bibliotheque>
  <livre style="fantaisie">
    <auteur>George R. R. MARTIN</auteur>
    <titre>A Game Of Thrones</titre>
    <langue>klingon</langue>
    <prix>10.17</prix>
  </livre>
  <livre style="aventure">
    <auteur>Alain Damasio</auteur>
    <titre>La Horde Du Contrevent</titre>
    <prix devise="euro">9.40</prix>
    <recommandation note="20"/>
  </livre>
</bibliotheque>
```

- **&lt;livre style="fantaisie"&gt;** : balise, elle a un attribut style="fantaisie".

Dans un fichier XML, une hiérarchie peut être créée en plaçant des nœuds à l’intérieur d’autres nœuds.在 XML 文件中，可以通过将节点置于其他节点内来创建层次结构。
Un nœud parent encapsule d’autres nœuds.父节点封装其他节点。
Les nœuds enfants sont contenus dans un nœud parent.子节点包含在父节点中。

## **5. Types de ressources dans Android / Android 资源类型**

| **Dossier / 目录** | **Description / 说明** | **Contenu / 内容** | **Analyse syntaxique / 语法分析** |
|-------------|------------------|-------------|------------------|
| `res/drawable/` | Images et dessins XML / 设计和图像 | `.png`, `.jpg`, `.xml` | **Oui** / 是 |
| `res/layout/` | Interfaces utilisateur XML / 页面布局或图形界面 | `.xml` (Disposition des vues) | **Exclusivement** |
| `res/menu/` | Menus de l'application / 菜单 | `.xml` | **Exclusivement** |
| `res/values/` | Variables et chaînes de caractères / 不同的变量 | `strings.xml`, `colors.xml` | **Exclusivement** |
| `res/raw/` | Fichiers de données brutes / 原始数据 | `.mp3`, `.html` | **Le moins possible** |

**Exclusivement** : Si la ressource ne contient que des fichiers XML.完全：如果资源只包含 XML 文件。
**Oui** : Si elle peut contenir d'autres types de fichiers en fonction des besoins (ex. drawable/ peut contenir des images ou XML).是：如果可以根据需要包含其他文件类型（例如 drawable/ 可以包含图像或 XML）。
**Le moins possible** : Si XML n'est pas recommandé, car d'autres répertoires sont mieux adaptés (ex. raw/ est pour les fichiers qui ne trouvent pas leur place ailleurs).尽可能少：不建议使用 XML，因为其他目录更合适（例如， raw/ 用于存放不适合放在其他地方的文件）。

![alt text](image-1.png)

- **Les ressources sont organisées dans des répertoires spécifiques pour faciliter l’adaptation aux différents écrans et langues.**  
- **资源被组织在特定的目录中，使其更容易适应不同的屏幕和语言。**

---

## **6. Organisation avancée des ressources**

📌 **Android permet de gérer différentes ressources selon :**  
📌 **Android 允许根据以下条件管理不同的资源：**

1. **La résolution d’écran** (`drawable-hdpi`, `drawable-mdpi`, `drawable-xhdpi`).  
   **屏幕分辨率**
2. **L’orientation de l’écran** (`layout-land` pour paysage, `layout-port` pour portrait).  
   **屏幕方向**
3. **La langue et la région** (`values-fr`, `values-en`, `values-zh-rCN`).  
   **语言和地区**（ `values-fr` 为法语，`values-en` 为英语，`values-zh-rCN` 为简体中文）。

