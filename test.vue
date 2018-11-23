// 测试生成文档组件
// 书写规范
// - 所有$emit不能直接写在template标签中，同名$emit，将读取第一次出现时注释作为说明
// - props不能使用 props:[xxx, xxx, xxx]形式，必须至少指定类型

// TODO
// - props的default基于其他prop的值？？
// - slot更详细的解析：比如绑定属性、默认结构
// - 组件name解析 & 组件额外说明解析

/** @doc
**aaaa  */

// @doc

<template>
    <div class="wrapper">
        <div class="inner">
            <!-- @doc 内部插槽 -->
            <slot name="inner"></slot>
            <!-- @doc 绑定其他属性的插槽 -->
            <slot name="scoped" :todo="todo" v-show="testbind">
                <h1>xxxxxx</h1>
            </slot>
        </div>
        <!-- @doc 默认插槽 -->
        <slot></slot>
    </div>
</template>
<script>
export default {
    name: 'testComponent',
    props: {
        //@doc 仅指定类型：单类型
        // @doc 第二行
        /**
         * @docbegin block
         * lalalal
         * @docend
         */
        type: String,
        //@doc 仅指定类型：多类型
        multiple: [String, Number],
        //@doc 指定类型&默认值
        defaultString: {
            type: String,
            default: 'test-default-string-value'
        },
        //@doc 默认值是一个函数
        functionDefault: {
            type: Array,
            // @doc 默认值设置为[1,2,3,4]
            default: () => {
                return [1, 2, 3, 4];
            }
        },
        //@doc 指定是否必填
        disabled: {
            type: Boolean,
            default: false,
            required: true
        },
        //@doc 指定validate
        maxlength: {
            type: Number,
            default: 100,
            //@doc 返回数字
            validator: function(value) {
                return value >= 0;
            }
        }
    },
    data() {
        return {
            todo: {},
            testbind: []
        };
    },
    methods: {
        // @doc 对外API
        // @doc 多行
        /**
         * @doc block级别
         */
        getValue() {
            return this.currentValue;
        },
        _onInput(event) {
            // @doc 输入事件，参数为当前输入框的值
            this.$emit('input', value);
        },
        _onBlur(event) {
            // @doc 失焦事件，参数为当前输入框的值
            this.$emit('blur', this.currentValue);
        },
        _onFocus(event) {
            this.isFocus = true;
            // @doc 聚焦事件，参数为当前输入框的值
            this.$emit('focus', this.currentValue);
        },
        _onDelete(event) {
            this.setCurrentValue('');
            // @doc 后出现的$emit input，这段注释将被忽略
            this.$emit('input', '');
            // @doc 清空输入框事件
            this.$emit('delete');
        }
    }
};
</script>