# Emoji 映射关系仓库说明

## 简介
本仓库包含一个文件，该文件定义了文字与 emoji 之间的映射关系。这些映射信息详细记录了每个 emoji 的相关属性，如名称、关键词、表情符号、统一编码等，方便开发者根据需求将文字与对应的 emoji 进行关联，只需对代码进行简单改进即可投入使用。

## 文件结构
仓库中仅有一个文件，文件内是一系列的 emoji 映射信息，每个映射信息以对象的形式呈现，包含以下属性：
- **id**：emoji 的唯一标识符，可用于在代码中引用该 emoji。
- **name**：emoji 的中文名称，方便用户识别。
- **keywords**：与该 emoji 相关的关键词列表，包含中文和英文，用于更广泛的匹配和搜索。
- **emoticons**（部分有）：该 emoji 对应的表情符号，如 `:D` 对应咧嘴笑的表情。
- **skins**：emoji 的皮肤信息，包含统一编码 `unified` 和原生显示字符 `native`。
- **version**：emoji 信息的版本号，目前均为 1。

## 示例代码片段
以下是文件中的部分代码示例，展示了几个 emoji 的映射关系：
```javascript
100: {
    id: "100",
    name: "一百分",
    keywords: ["得分", "完美", "数字", "世纪", "考试", "测验", "测试", "通过", "百分点", "一百分", "满分", "100", "score", "perfect", "numbers", "century", "exam", "quiz", "test", "pass"],
    skins: [{
        unified: "1f4af",
        native: "💯"
    }],
    version: 1
},
1234: {
    id: "1234",
    name: "输入数字",
    keywords: ["蓝色", "广场", "青", "正方形", "输入数字", "入力番号", "打字", "1234", "blue", "square"],
    skins: [{
        unified: "1f522",
        native: "🔢"
    }],
    version: 1
},
grinning: {
    id: "grinning",
    name: "嘿嘿",
    emoticons: [":D"],
    keywords: ["微笑", "快乐", "喜悦", "笑", "笑脸", "嘿嘿", "脸", "smile", "happy", "joy", ":D", "grin", ":d", "：D", "d", ": D", "Grin"],
    skins: [{
        unified: "1f600",
        native: "😀"
    }],
    version: 1
}
```

## 使用方法
### 简单使用
如果你只是想查看文字与 emoji 的映射关系，可以直接打开文件查看其中的内容。

### 代码集成
若要在代码中使用这些映射关系，你可以根据具体需求对代码进行简单改进。以下是一个简单的 JavaScript 示例，展示如何根据关键词查找对应的 emoji：
```javascript
// 假设以下是从文件中读取的映射数据
const emojiMapping = {
    100: {
        id: "100",
        name: "一百分",
        keywords: ["得分", "完美", "数字", "世纪", "考试", "测验", "测试", "通过", "百分点", "一百分", "满分", "100", "score", "perfect", "numbers", "century", "exam", "quiz", "test", "pass"],
        skins: [{
            unified: "1f4af",
            native: "💯"
        }],
        version: 1
    },
    1234: {
        id: "1234",
        name: "输入数字",
        keywords: ["蓝色", "广场", "青", "正方形", "输入数字", "入力番号", "打字", "1234", "blue", "square"],
        skins: [{
            unified: "1f522",
            native: "🔢"
        }],
        version: 1
    },
    grinning: {
        id: "grinning",
        name: "嘿嘿",
        emoticons: [":D"],
        keywords: ["微笑", "快乐", "喜悦", "笑", "笑脸", "嘿嘿", "脸", "smile", "happy", "joy", ":D", "grin", ":d", "：D", "d", ": D", "Grin"],
        skins: [{
            unified: "1f600",
            native: "😀"
        }],
        version: 1
    }
};

function findEmojiByKeyword(keyword) {
    for (const emojiId in emojiMapping) {
        const emoji = emojiMapping[emojiId];
        if (emoji.keywords.includes(keyword)) {
            return emoji.skins[0].native;
        }
    }
    return null;
}

// 示例使用
const keyword = "完美";
const emoji = findEmojiByKeyword(keyword);
if (emoji) {
    console.log(`找到对应的 emoji: ${emoji}`);
} else {
    console.log(`未找到与关键词 "${keyword}" 对应的 emoji。`);
}
```

## 贡献
如果你发现映射关系有误或想添加新的 emoji 映射，可以提交 Pull Request 进行修改。请确保在修改时遵循现有的数据格式。
