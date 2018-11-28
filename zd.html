import React, { Component } from 'react'
// import {bindActionCreators} from 'redux' import {connect} from 'react-redux'
import './FilterAlertComponent.scss'

const makeUID = () => {
    let count = 0,
        numcount = 0;
    let uid = [];
    while (count < 3) {
        uid.push(String.fromCharCode(97 + Math.random() * 26))
        count++;
    }
    while (numcount < 3) {
        uid.push(parseInt((Math.random() * 10), 0));
        numcount++;
    }
    return uid.join('');
}
//升序
const SortAsc = (a, b) => {
    return a.order > b.order ? 1 : -1;
}
export default class FilterAlertComponent extends Component {
    constructor(props) {
        super(props);
        let newState = this.updateData(props);
        newState.randomVariable = makeUID();
        newState.randomVariable2 = makeUID();
        newState.redBorder = false;
        newState.redBorder2 = false;
        newState.redBorder3 = false;
        this.state = newState;
        // 取消时，用这个数据刷新state
        this.reset = jtools.clone(newState);
    }
    updateData = (props) => {
        // 自定义 : custom ; 时间 : time ; 周 : week ; 分段 : subsection
        let { data } = props, { displayMode } = data,
            choiceData = data[displayMode],
            unitIndex = 0,
            linkIndex = 0,
            indexObj = this.getIndex(choiceData.items, unitIndex, linkIndex),
            newState = {
                ...data,
                addUnitName: '', // 添加转换单位的名称
                addUnitValue: '', // 添加转换单位的值
                addExpression: indexObj.addExpression, // 添加转换单位的表达式
                unitIndex: indexObj.unitIndex, // 有单位转换的索引值
                linkIndex: indexObj.linkIndex, // 有关联关系的索引值
                addUnitIsShow: false, // 是否显示单位转换模块
                addLinkIsShow: false, // 是否显示关联模块
                addCombinationIsShow: false, // 是否显示单位，关联模块
                SortVariables: [] //存排序组件变量
            };
        return newState
    }
    // update
    componentDidUpdate(nextProps) {
        let flag = jtools.isEqualToObj(nextProps, this.props);
        if (!flag) {
            let { data } = this.props,
                newState = this.updateData(this.props);
            this.setState({
                ...newState
            });
        }
        return true
    }
    // 获取有转换单位，关联值的相关
    getIndex = (data, unitIndex, linkIndex) => {
        let { addCombinationIndex = 0 } = this.props;
        let unitIndexArr = [],
            linkIndexArr = [];
        data.forEach((item, index) => {
            if (item.hasUnit) {
                unitIndexArr[unitIndexArr.length] = index;
            }
            if (item.hasLink) {
                linkIndexArr[linkIndexArr.length] = index;
            }
        })
        // 有转换单位的索引值
        unitIndex = (unitIndex !== 0) ? unitIndex : (unitIndexArr[addCombinationIndex] || 0);
        // 有关联关系的索引值
        linkIndex = (linkIndex !== 0) ? linkIndex : (linkIndexArr[addCombinationIndex] || 0);
        return { unitIndex, linkIndex }
    }
    // 下拉组件事件
    choiceComponent = (obj, index, areaName) => {
        if (index !== undefined) { // 有索引值的为条件内容，没有索引值的是展示的条件类型
            let { displayMode, addUnitValue, alertComponent, addCombinationIndex } = this.state, // 当前的展示模块的key值
                updateData = this.state[displayMode],
                updateRow = updateData.items[index], // 修改当前行的数据
                areaObj = displayMode === 'subsection' ? alertComponent[displayMode][addCombinationIndex].items[index] : alertComponent[displayMode].items[index];
            if (areaName === 'AddCombination') {
                let selectIndex = 0;
                let optionsKey = areaObj.unitOptions ? 'unitOptions' : 'options';
                let fieldKey = (displayMode === 'time' || displayMode === 'inclination') ? 'value' : 'key';
                areaObj[optionsKey].forEach((item, ind) => {
                    areaObj[optionsKey][ind].isSelectd = false;
                    areaObj[optionsKey][ind].show = false;
                    if (item[fieldKey] === obj.value) {
                        areaObj.selectValue = item[fieldKey]; // 下拉选择的value
                        areaObj[optionsKey][ind].isSelectd = true; // 下拉选项的选中标记
                        areaObj[optionsKey][ind].show = true; // 下拉选项的选中标记
                    }
                })
                if (displayMode === 'subsection') {
                    alertComponent[displayMode][addCombinationIndex].items[index] = areaObj;
                } else {
                    alertComponent[displayMode].items[index] = areaObj;
                }
                this.setState({ alertComponent });
            } else {
                let optionsKey = updateRow.unitOptions ? 'unitOptions' : 'options';
                updateRow[optionsKey].forEach((item, ind) => {
                    // 遍历时让每一个选项都改成非选中
                    updateRow[optionsKey][ind].isSelectd = false;
                    updateRow[optionsKey][ind].show = false;
                    if (item.value === obj.value) {
                        updateRow.ComponentType = item.ComponentType; // 行组件展示类型
                        updateRow.selectValue = obj.value; // 下拉选择的value
                        updateRow.manageStyle === 'OPERATOR' && (updateRow.value = obj.value); // 下拉选择的value
                        updateRow[optionsKey][ind].isSelectd = true; // 下拉选项的选中标记
                        updateRow[optionsKey][ind].show = true; // 下拉选项的选中标记
                    }
                });
                if (displayMode === 'custom' && updateRow.manageStyle === 'OPERATOR') { //如果有filter时，修改操作符需要将filter中的operator替换
                    let filter = updateData.items[3].filter;
                    if (filter) {
                        filter.operator = obj.value;
                    }
                }
                this.setState({ [displayMode]: updateData, addUnitValue });
            }
        } else {
            // 没有索引值 则为选择模块组件
            let data = jtools.clone(this.state), { choiceRow, displayMode } = data,
                type = displayMode;
            //切换模块
            if (areaName === 'choiceRow') {
                choiceRow.unitOptions.forEach((item, ind) => {
                    choiceRow.unitOptions[ind].isSelectd = false;
                    if (item.value === obj.value) {
                        type = item.type;
                        choiceRow.selectValue = obj.value;
                        choiceRow.unitOptions[ind].isSelectd = true;
                    }
                });
                // 初始化有添加转换的索引值
                let choiceData = data[type],
                    indexObj = (choiceData && choiceData.items) ? this.getIndex(choiceData.items, 0, 0) : {};
                this.setState({
                    choiceRow,
                    displayMode: type,
                    unitIndex: indexObj.unitIndex || 0,
                    linkIndex: indexObj.linkIndex || 0,
                    addExpression: indexObj.addExpression,
                    addUnitIsShow: false,
                    addLinkIsShow: false,
                    addCombinationIsShow: false
                });
            } else if (areaName === 'table') {
                let { tableList, fieldList, custom } = data,
                    filter = custom.items[3].filter;
                if (obj.value !== '$undefined') {
                    let tableObj = tableList.unitOptions.find(item => item.name === obj.value);
                    tableList.selectValue = obj.value;
                    fieldList.unitOptions = tableObj.fields;
                    fieldList.selectValue = '';
                    if (filter) {
                        filter.field.ref.table.id = tableObj.id;
                        filter.field.ref.table.name = tableObj.name;
                    } else {
                        let fieldObj = tableObj.fields[1];
                        let filterObj = {
                            "union": "and",
                            "field": {
                                "type": "COLUMN",
                                "ref": {
                                    "type": fieldObj.item.type_value,
                                    "id": fieldObj.item.id,
                                    "name": fieldObj.item.name,
                                    "table": {
                                        "id": tableObj.id,
                                        "name": tableObj.name
                                    }
                                }
                            },
                            "value": "${" + (custom.items[3].name || this.props.uuid) + "}",
                            "operator": custom.items[2].value
                        };
                        custom.items[3].filter = filterObj;
                    }
                } else {
                    delete custom.items[3].filter;
                    tableList.selectValue = '';
                    fieldList.unitOptions = tableList.unitOptions[0].fields;
                    fieldList.selectValue = '';
                }
                this.setState({ tableList, fieldList, custom });
            } else if (areaName === 'field') {
                let { tableList, fieldList, custom } = data,
                    filter = custom.items[3].filter;
                if (obj.value !== '$undefined') {
                    let fieldObj = fieldList.unitOptions.find(item => item.name === obj.value);
                    fieldList.selectValue = obj.value;
                    if (filter) {
                        filter.field.ref.id = fieldObj.item.id;
                        filter.field.ref.name = fieldObj.item.name;
                        filter.field.ref.type = fieldObj.item.type_value;
                    }
                } else {
                    delete custom.items[3].filter;
                    tableList.selectValue = '';
                    fieldList.unitOptions = tableList.unitOptions[0].fields;
                    fieldList.selectValue = '';
                }
                this.setState({ tableList, fieldList, custom });
            } else {
                // 改变模式
                let modeData = data[areaName],
                    choiceData = data[type];
                modeData.unitOptions && modeData.unitOptions.forEach((item, ind) => {
                    modeData.unitOptions[ind].isSelectd = false;
                    if (item.value === obj.value) {
                        modeData.processMode = item.value;
                        modeData.selectValue = item.value;
                        modeData.unitOptions[ind].isSelectd = true;
                        choiceData.processMode = item.value;
                    }
                });
                this.setState({ [areaName]: modeData, [type]: choiceData });
            }
        }

    }
    // 输入框事件
    BlurInput = (obj, index, type) => {
        let { displayMode } = this.state,
            updateData = this.state[displayMode];
        if (index !== undefined) {
            updateData.items[index][type] = obj.value;
            if (index === 3 && type === 'value') {
                updateData.items[index].name = this.props.uuid;
            }
            this.setState({ [displayMode]: updateData });
        } else {
            let val = obj.value;
            if (type === 'addExpression' && val) { //校验公式
                if (val.includes('${value}')) {
                    let reg = /^\d+(\.*\d{0,2})([+*/-]\d+(\.*\d{0,2}))+$/;
                    let rval = obj.value.replace('${value}', '100');
                    if (reg.test(rval)) {
                        this.setState({ [type]: obj.value });
                    } else {
                        alert(i18n.message("FILTER.ALERT.ROW.FORMULAWRONG"));
                    }
                } else {
                    alert(i18n.message("FILTER.ALERT.ROW.FORMULAWRONG"));
                }
            } else {
                this.setState({ [type]: obj.value });
            }
        }
    }
    // 输入框事件
    changeInput = (obj, index, type, areaName) => {
        let { displayMode, alertComponent, addCombinationIndex } = jtools.clone(this.state),
            updateData = this.state[displayMode];
        // 添加关联，单位，分段区域模块处理
        if (areaName === 'AddCombination') {
            let areaObj = {};
            if (displayMode === 'subsection') {
                areaObj = jtools.clone(alertComponent[displayMode][addCombinationIndex]);
            } else {
                areaObj = jtools.clone(alertComponent[displayMode]);
            }
            areaObj.items[index][type] = obj.value;
            if (displayMode === 'subsection') {
                alertComponent[displayMode][addCombinationIndex] = areaObj;
            } else {
                alertComponent[displayMode] = areaObj;
            }
            this.setState({ alertComponent });
        } else {
            if (index !== undefined) {
                updateData.items[index][type] = obj.value;
                let valItem = updateData.items.find(item => item.manageStyle === 'VALUE');
                if (valItem && (type === 'offset' || type === 'limit')) {
                    valItem[type] = obj.value;
                }
                if (index === 3 && type === 'value') {
                    updateData.items[index].name = this.props.uuid;
                }
                if (type === 'value' || type === 'rawValue') {
                    updateData.items[index].defaultValue = obj.value;
                }
                if (displayMode === 'custom' && type === 'rawValue') {
                    let options = updateData.items[5].options;
                    if (options.length && /^[0-9]*\.?[0-9]+$/.test(obj.value)) {
                        let formula = options[0] ? (options[0].formula || '${value}*1') : '${value}*1';
                        let rval = formula.replace('${value}', obj.value || 0);
                        updateData.items[index].value = eval(rval);
                    } else {
                        updateData.items[index].value = obj.value;
                    }
                }
                this.setState({ [displayMode]: updateData });
            } else {
                this.setState({ [type]: obj.value });
            }
        }

    }

    getAddObj = (data, str, obj) => {
        if (str.indexOf('Value') >= 0) {
            obj.value = data[str];
        } else if (str.indexOf('Offset') >= 0) {
            obj.offset = data[str];
        } else if (str.indexOf('Limit') >= 0) {
            obj.limit = data[str];
        } else if (str.indexOf('Varible') >= 0) {
            obj.variable = data[str];
        } else if (str.indexOf('name') >= 0) {
            obj.name = data[str];
        } else if (str.indexOf('Select') >= 0) {
            obj.options = data[str];
        }
        return obj
    }
    // 添加单位&添加关联
    addUnit = (isEdit, isEditIndex,isArray) => {
        let data = jtools.clone(this.state), {
            displayMode,
            alertComponent,
            addCombinationIndex,
            randomVariable,
            unitIndex,
            SortVariables,
            randomVariable2,
            addCombinationIsShow
        } = data,
            displayModeData = data[displayMode],
            addData = displayMode === 'subsection' ? alertComponent[displayMode][addCombinationIndex].items : alertComponent[displayMode].items, //添加的数据
            addObj = {},
            addFlag = true;
        if(isArray["preVarible"]==false){
            addData[1].value='';
            addData[2].value='';
            addData[3].value='';
        }
        if(isArray["nextVarible"]==false){
            addData[6].value='';
            addData[7].value='';
            addData[8].value='';
        }

        if (addData.length) {
            for (let i = 0; i < addData.length; i++) {
                let item = addData[i];
                 // add zhangda 11.9
                    if(addCombinationIndex==1){//根据数据长度判断是不是分段
                        if(isArray["preVarible"]==false&&isArray["nextVarible"]==false){
                            alert(i18n.message("CASEDETAIL.DIALOG.TITLE.ATLEAST"));
                            addFlag = false;
                            item.redBorder = true;
                            break;
                        }else if(item.display == 'hide'&&isArray["nextVarible"]==false){
                            if(i<5){
                                alert(i18n.message("CASEDETAIL.DIALOG.TITLE.ATLEAST"));
                                addFlag = false;
                                item.redBorder = true;
                                break;
                            }
                           
                        }
                    } 
                 // end
                if (item.ComponentType === 'input' || item.ComponentType === 'textArea') { //textArea
                    // 输入框类型
                    if ((item.value === ''||item.value === undefined) && item.display !== 'hide') {
                        if(isArray['preVarible']==true&&isArray['nextVarible']==true){
                            alert(i18n.message("FILTER.ALERT.ROW.NOTEMPTY"));
                            addFlag = false;
                            item.redBorder = true;
                            break;
                        }else if(isArray['preVarible']==true&&isArray['nextVarible']==false){
                            if(i<5){
                                alert(i18n.message("FILTER.ALERT.ROW.NOTEMPTY"));
                                addFlag = false;
                                item.redBorder = true;
                                break;
                            }
                        }else if(isArray['preVarible']==false&&isArray['nextVarible']==true){
                            if(i>=5){
                                alert(i18n.message("FILTER.ALERT.ROW.NOTEMPTY"));
                                addFlag = false;
                                item.redBorder = true;
                                break;
                            }
                        }
                        
                    } else {
                        if ((item.submitType === 'key' || item.submitType === 'name') && item.display !== 'hide') {
                            let StrReg = /^[0-9a-zA-Z\u4e00-\u9fa5]/;//验证非法字符 如<alert></alert>
                            if (StrReg.test(item.value)) {
                                addObj.key = item.value;
                                addObj.name = item.value;
                            }
                            else {
                                alert(i18n.message("ENTITY_MANAGE.NEWENTITY.ERRORFORMAT"));
                                addFlag = false;
                                item.redBorder = true;
                                break;
                            }
                        } else {
                            let getValue = '';
                            if (item.submitType === 'formula' && item.display !== 'hide') { // 公式
                                if (item.value.includes('${value}')) {
                                    let reg = /^\d+(\.*\d{0,2})([+*/-]\d+(\.*\d{0,2}))+$/;
                                    let rval = item.value.replace('${value}', '100');
                                    if (!reg.test(rval)) {
                                        alert(i18n.message("FILTER.ALERT.ROW.EXPRESSIONWRONG"));
                                        addFlag = false;
                                        item.redBorder = true;
                                        break
                                    }
                                } else {
                                    alert(i18n.message("FILTER.ALERT.ROW.EXPRESSIONWRONG") + '${value}*1024');
                                    addFlag = false;
                                    item.redBorder = true;
                                    break
                                }
                            }
                            else if ((item.submitType === 'value' || item.submitType === 'offset' || item.submitType === 'limit') && item.display !== 'hide') {
                                //@author:zhangjieliang @date:2017/6/29 10:35 @comment:修改55881
                                let reg1 = /^\d+(\.\d+)?$/;//验证非负数 0 整数
                                // let reg2 = /^(([0-9]+)|([0-9]+\.[0-9]{1,2}))$/;//验证非负数,小数保留2位
                                if (!reg1.test(item.value)) {
                                    alert(i18n.message("FILTER.ALERT.ROW.INTEGER"));
                                    addFlag = false;
                                    item.redBorder = true;
                                    break
                                }
                            }
                            else if ((item.submitType.indexOf('Value') > -1 || item.submitType.indexOf('Offset') > -1 || item.submitType.indexOf('Limit') > -1) && item.display !== 'hide') {
                                let reg1 = /^\d+(\.\d+)?$/;//验证非负数 0 整数
                                if (!reg1.test(item.value)) {
                                    alert(i18n.message("FILTER.ALERT.ROW.INTEGER"));
                                    addFlag = false;
                                    item.redBorder = true;
                                    break
                                }
                            }
                            (item.display !== 'hide') && (addObj[item.submitType] = item.value);
                        }
                    }
                } else if (item.ComponentType === 'select' && item.display !== 'hide') {
                    // 下拉框类型
                    if (displayMode === 'subsection' && addCombinationIndex === '1') {
                        addObj[item.submitType] = jtools.extend(true,{},item.unitOptions || item.options);
                    } else {
                        addObj[item.submitType] = item.selectValue === '' ? item.unitOptions[0].value : item.selectValue;
                    }
                } else if (item.ComponentType === 'label' && item.display !== 'hide') {
                    // 变量类型
                    if (displayMode === 'subsection' || displayMode === 'inclination') {
                        addObj[item.submitType] = isEdit ? item.value : (item.submitType === "preVarible" ? randomVariable : randomVariable2);
                    }
                    else {
                        addObj[item.submitType] = isEdit ? item.value : randomVariable;
                    }
                } else if (item.ComponentType === 'checkbox' && item.display !== 'hide') {
                    // 变量类型
                    addObj[item.submitType] = !!item.show;
                }
            }
            let unitOptions = displayModeData.items[unitIndex].options,
                flag = true;
            if (!isEdit) {
                for (let i = 0; i < unitOptions.length; i++) {
                    let item = unitOptions[i];
                    if (displayMode === 'subsection') {
                        if (addCombinationIndex !== '1') {
                            if (addObj.key === item.key) {
                                flag = false;
                                alert(i18n.message("FILTER.ALERT.ROW.NOTSAME"));
                                break
                            }
                        }
                    } else if (displayMode !== 'inclination') {
                        if (addObj.key === item.key) {
                            flag = false;
                            alert(i18n.message("FILTER.ALERT.ROW.NOTSAME"));
                            break
                        }
                    }
                }
            }
            if (addFlag) {
                let dealAddObj = false;
                if (displayMode === 'subsection') {
                    if (addCombinationIndex === '0') { // 模型结构不能改变
                        alertComponent[displayMode][1].items[4].options = jtools.clone(displayModeData.items[unitIndex].options) || [];
                        alertComponent[displayMode][1].items[9].options = jtools.clone(displayModeData.items[unitIndex].options) || [];
                        alertComponent[displayMode][1].items[4].options.push(addObj);
                        alertComponent[displayMode][1].items[9].options.push(addObj);
                    } else if (addCombinationIndex === '1') {
                        let pre = {},
                            next = {};
                        for (let item in addObj) {
                            if (item.indexOf('pre') >= 0) {
                                pre = this.getAddObj(addObj, item, pre);
                            } else if (item.indexOf('next') >= 0) {
                                next = this.getAddObj(addObj, item, next);
                            }
                        }
                        addObj.preVarible && (pre.options = alertComponent[displayMode][1].items[4].options);
                        next.options = alertComponent[displayMode][1].items[9].options;
                        dealAddObj = {
                            item: [
                                {
                                    ...pre
                                }, {
                                    ...next
                                }
                            ]
                        };
                    }
                }
                if (isEdit) { //编辑
                    if (displayMode === 'subsection' && addCombinationIndex === '1') {
                        displayModeData.items[unitIndex].options[isEditIndex].item = dealAddObj.item;
                        //add zd 编辑的时候再重新添加一下
                        dealAddObj.item[1].value&&(SortVariables.push({ name: dealAddObj.item[1].variable, value: dealAddObj.item[1].value, type: displayMode.toUpperCase(), quoteNum: 0 }));
                    }
                    else {
                        jtools.extend(true, displayModeData.items[unitIndex].options[isEditIndex], addObj);
                    }
                    this.setState({ alertComponent, [displayMode]: displayModeData, SortVariables });
                }
                else {//新增
                    if (!displayModeData.items[unitIndex].options) {
                        displayModeData.items[unitIndex].options = [];
                    }
                    let optionLength = displayModeData.items[unitIndex].options.length;
                    if (flag) {
                        if (displayMode === 'subsection' && addCombinationIndex === '1') {
                            if (optionLength >= 10) {
                                alert(i18n.message("FILTER.ALERT.ROW.MUSTBEFIVE"));
                                return
                            }
                            if (optionLength === 0) {
                                dealAddObj.position = 'first';
                                dealAddObj.order = 1;
                                alertComponent[displayMode][1].items.forEach((item, ind) => {
                                    if (item.submitType.indexOf('pre') >= 0) {
                                        alertComponent[displayMode][1].items[ind].display = 'hide';
                                    }
                                });
                            } else {
                                let firstFlag = true,
                                    lastFlag = true;
                                displayModeData.items[unitIndex].options.forEach(item => {
                                    if (item.position === 'first') {
                                        firstFlag = false;
                                    }
                                    if (item.position === 'last') {
                                        lastFlag = false;
                                        item.order = 10;
                                    }
                                });
                                if (!firstFlag && lastFlag) {
                                    dealAddObj.position = 'last';
                                    dealAddObj.order = 10;
                                }
                                if (firstFlag) {
                                    dealAddObj.position = 'first';
                                    dealAddObj.order = 1;
                                }
                                if (!firstFlag && !lastFlag) {
                                    dealAddObj.order = optionLength;
                                }
                                alertComponent[displayMode][1].items.forEach((item, ind) => {
                                    delete alertComponent[displayMode][1].items[ind].display;
                                    delete alertComponent[displayMode][1].items[ind].disable;
                                    alertComponent[displayMode][1].items[ind].value = '';
                                    if (firstFlag) {
                                        if (lastFlag) { //没有第一行，也没有最后一行
                                            if (item.submitType.indexOf('pre') >= 0) {
                                                alertComponent[displayMode][1].items[ind].display = 'hide';
                                            }
                                        }
                                    } else {
                                        if (lastFlag) { // 有第一行，没有最后一行
                                            if (item.submitType.indexOf('pre') >= 0) {
                                                delete alertComponent[displayMode][1].items[ind].display
                                            }
                                        }
                                    }
                                });
                            }
                        }
                        displayModeData.items[unitIndex].options[optionLength] = dealAddObj ? dealAddObj : addObj;
                        displayModeData.items[unitIndex].options.sort(jtools.sortFunction('order', false));
                        // //将排序组件的变量push进secondVariables
                        if (displayMode === 'sort' || displayMode === 'flowRatio') {
                            SortVariables.push({ name: randomVariable, value: addObj.key, type: displayMode.toUpperCase(), quoteNum: 0 });
                        }
                        else if (displayMode === 'subsection' && dealAddObj) {
                            dealAddObj.item[0].value && (SortVariables.push({ name: randomVariable, value: dealAddObj.item[0].value, type: displayMode.toUpperCase(), quoteNum: 0 }));
                            dealAddObj.item[1].value&&(SortVariables.push({ name: randomVariable2, value: dealAddObj.item[1].value, type: displayMode.toUpperCase(), quoteNum: 0 }));
                        }
                        else if (displayMode === 'inclination') {
                            SortVariables.push(
                                { name: randomVariable, value: addObj.preValue, type: displayMode.toUpperCase(), quoteNum: 0 },
                                { name: randomVariable2, value: addObj.nextValue, type: displayMode.toUpperCase(), quoteNum: 0 }
                            );
                        }
                        addData.forEach((elem, index) => {
                            addData[index].value = '';
                            addData[index].show = false;
                        });
                        randomVariable = makeUID();
                        randomVariable2 = makeUID();
                    }
                    this.setState({ alertComponent, [displayMode]: displayModeData, randomVariable, SortVariables, randomVariable2 });
                }
            }
        }
    }
    // 删除单位事件
    deleUnit = (index, type, callback) => {
        let {
            displayMode,
            unitIndex,
            linkIndex,
            SortVariables,
            addCombinationIndex,
            alertComponent
        } = this.state,
            { secondVariables = [], updateVariable } = this.props,
            choiceData = jtools.clone(this.state[displayMode]),
            arrIndex = type === 'link' ? linkIndex : unitIndex,
            unitArr = choiceData.items[arrIndex].options;
        let secondVariablesClone = jtools.clone(secondVariables);
        let isQuote = false;
        //将排序组件的变量secondVariables中对应的变量删除
        if (displayMode === 'sort' || displayMode === 'flowRatio' || displayMode === 'inclination' || displayMode === 'subsection') {
            let obj = unitArr[index];
            let vname = '', vname2 = '';
            if (displayMode === 'flowRatio') {
                vname = obj.name;
            }
            else if (displayMode === 'sort') {
                vname = obj.value;
            }
            else if (displayMode === 'subsection' && addCombinationIndex === '1') {
                vname = obj.item[1].variable;
                vname2 = obj.item[0].variable;
            }
            else if (displayMode === 'inclination') {
                vname = obj.nextVarible;
                vname2 = obj.preVarible;
            }
            let ind = SortVariables.findIndex(item => item.name === vname);
            let ind0 = vname2 ? SortVariables.findIndex(item => item.name === vname2) : -1;
            if (ind > -1) {
                SortVariables.splice(ind, 1);
                SortVariables.splice(ind0, 1);
            }
            else {
                let ind1 = secondVariablesClone.findIndex(item => item.name === vname);
                if (ind1 > -1 && !secondVariablesClone[ind1].quoteNum) {
                    secondVariablesClone.splice(ind1, 1);
                }
                else if (ind1 > -1) {
                    !isQuote && alert(i18n.message("FILTER.ALERT.ROW.NOTDELETE"));
                    isQuote = true;
                    callback && callback(isQuote);
                    return;
                }
                if (vname2) {
                    let ind2 = secondVariablesClone.findIndex(item => item.name === vname2);
                    if (ind2 > -1 && !secondVariablesClone[ind2].quoteNum) {
                        secondVariablesClone.splice(ind2, 1);
                    }
                    else if (ind2 > -1) {
                        !isQuote && alert(i18n.message("FILTER.ALERT.ROW.NOTDELETE"));
                        isQuote = true;
                        callback && callback(isQuote);
                        return;
                    }
                }
                secondVariables = secondVariablesClone;
                this.setState({ secondVariablesClone });
            }
        }
        unitArr.splice(index, 1);
        choiceData.items[arrIndex].options = unitArr;

        // 控制添加模块的显示
        if (displayMode === 'subsection' && addCombinationIndex === '1') {
            let firstFlag = true,
                lastFlag = true;
            if (choiceData.items[unitIndex].options.length === 0) {
                firstFlag = true;
                lastFlag = true;
            } else {
                choiceData.items[unitIndex].options.forEach(item => {
                    if (item.position === 'first') {
                        firstFlag = false;
                    }
                    if (item.position === 'last') {
                        lastFlag = false;
                    }
                });
            }

            alertComponent[displayMode][1].items.forEach((item, ind) => {
                delete alertComponent[displayMode][1].items[ind].display;
                delete alertComponent[displayMode][1].items[ind].disable;
                alertComponent[displayMode][1].items[ind].value = '';
               if (firstFlag) { //没有第一行的情况
                    if (item.submitType === 'preOffset') {
                        alertComponent[displayMode][1].items[ind].disable = true;
                        alertComponent[displayMode][1].items[ind].value = '0';
                    } else if (item.submitType === 'preValue') {
                        alertComponent[displayMode][1].items[ind].disable = true;
                        alertComponent[displayMode][1].items[ind].value = '0';
                    } else if (item.submitType === 'preLimit') {
                        alertComponent[displayMode][1].items[ind].disable = true;
                        alertComponent[displayMode][1].items[ind].value = '100';
                    }
               }
                if (!firstFlag && lastFlag) { // 没有最后一行的情况
                    if (item.submitType.indexOf('pre') >= 0) {
                        alertComponent[displayMode][1].items[ind].display = 'hide';
                    }
                }
            });
        }

        this.setState({ [displayMode]: choiceData, SortVariables, alertComponent });
        callback && callback(isQuote);
    }
    // 关联模块&&单位转换模块弹出控制
    alertUnitComponent = (flag, type, addCombinationIndex) => {
        let newState = jtools.clone(this.state), { unitIndex, linkIndex, displayMode, alertComponent } = newState,
            filterData = newState[displayMode],
            isShow = false;
        if (displayMode === 'subsection') { // 分段组件有两行有options
            if (filterData.items[1].options.length) {
                filterData.items[1].options.sort(SortAsc).forEach((item, index) => {
                    filterData.items[1].options[index].show = false;
                    if (index === 0) {
                        filterData.items[1].options[0].show = true;
                        if (addCombinationIndex === '1') {
                            alertComponent[displayMode][1].items[4].selectValue = filterData.items[1].options[0].key;
                            alertComponent[displayMode][1].items[9].selectValue = filterData.items[1].options[0].key;
                        }
                    }
                });
            }
            if (filterData.items[2].options.length) {
                filterData.items[2].options.forEach((item, index) => {
                    filterData.items[2].options[index].show = false;
                });
                filterData.items[2].options[0].show = true;
            }
        } else if (displayMode !== 'flowRatio') {
            if (filterData.items[unitIndex].options.length) {
                filterData.items[unitIndex].options.forEach((item, index) => {
                    filterData.items[unitIndex].options[index].show = false;
                });
                filterData.items[unitIndex].options[0].show = true;
            }
        }
        if (flag === 'hide') {
            isShow = false;
        } else if (flag === 'add') {
            let unitIndexArr = [],
                linkIndexArr = [];
            newState[displayMode].items.forEach((item, index) => {
                if (item.hasUnit) {
                    unitIndexArr[unitIndexArr.length] = index;
                }
                if (item.hasLink) {
                    linkIndexArr[linkIndexArr.length] = index;
                }
            });
            if (addCombinationIndex === '1') {
                // 有转换单位的索引值
                unitIndex = unitIndexArr[addCombinationIndex] || 0;
                // 有关联关系的索引值
                linkIndex = linkIndexArr[addCombinationIndex] || 0;
                if (newState.subsection.items[1].options && newState.subsection.items[1].options.length === 0) {
                    alert(i18n.message("FILTER.ALERT.ROW.ADDUNIT"));
                    return;
                } else {
                    let optionsData = filterData.items[unitIndex].options;
                    if (optionsData.length === 0) {
                        alertComponent[displayMode][1].items.forEach((item, ind) => {
                            delete alertComponent[displayMode][1].items[ind].display;
                            if (item.submitType === 'preOffset') {
                                alertComponent[displayMode][1].items[ind].disable = true;
                                alertComponent[displayMode][1].items[ind].value = '0';
                            } else if (item.submitType === 'preValue') {
                                alertComponent[displayMode][1].items[ind].disable = true;
                                alertComponent[displayMode][1].items[ind].value = '0';
                            } else if (item.submitType === 'preLimit') {
                                alertComponent[displayMode][1].items[ind].disable = true;
                                alertComponent[displayMode][1].items[ind].value = '100';
                            }
                        });
                    } else {
                        let lastFlag = true,
                            firstFlag = true;
                        optionsData.forEach((item, ind) => {
                            if (item.position === 'last') {
                                lastFlag = false;
                            } else if (item.position === 'first') {
                                firstFlag = false;
                            }
                        })
                        alertComponent[displayMode][1].items.forEach((item, ind) => {
                            delete alertComponent[displayMode][1].items[ind].display;
                            delete alertComponent[displayMode][1].items[ind].disable;
                            alertComponent[displayMode][1].items[ind].value = '';
                            if (firstFlag) {
                                delete alertComponent[displayMode][1].items[ind].display
                                if (item.submitType === 'preOffset') {
                                    alertComponent[displayMode][1].items[ind].disable = true;
                                    alertComponent[displayMode][1].items[ind].value = '0';
                                } else if (item.submitType === 'preValue') {
                                    alertComponent[displayMode][1].items[ind].disable = true;
                                    alertComponent[displayMode][1].items[ind].value = '0';
                                } else if (item.submitType === 'preLimit') {
                                    alertComponent[displayMode][1].items[ind].disable = true;
                                    alertComponent[displayMode][1].items[ind].value = '100';
                                }
                            }
                            if (lastFlag) {
                                if (item.submitType.indexOf('pre') >= 0) {
                                    alertComponent[displayMode][1].items[ind].display = 'hide';
                                }
                            }
                        });
                    }
                    isShow = !newState[type];
                }
            } else {
                unitIndex = unitIndexArr[0];
                isShow = !newState[type];
            }
        }
        this.setState({
            [type]: isShow,
            addCombinationIndex: addCombinationIndex || 0,
            [displayMode]: filterData,
            unitIndex,
            linkIndex,
            alertComponent
        });
    }
    // 取消事件
    cancle = (component, type) => {
        let resetData = jtools.clone(this.reset), { displayMode, unitIndex, addCombinationIndex } = this.state,
            cancelData = this.state[displayMode],
            resetUnit = jtools.clone(this.props).data[displayMode];
        if (component === 'alertCancle') { // 转换条件模块取消
            if (displayMode === 'subsection') {
                if (addCombinationIndex === '0') {
                    cancelData.items[1].options = resetUnit.items[1].options;
                } else if (addCombinationIndex === '1') {
                    cancelData.items[2].options = resetUnit.items[2].options;
                }
            } else {
                cancelData.items[unitIndex].options = resetUnit.items[unitIndex].options;
            }
            this.setState({ [type]: false, [displayMode]: cancelData });
        } else if (component === 'submitCancle') {
            let { isShowFilterComponent } = this.props;
            this.setState(resetData);
            isShowFilterComponent();
        }
    }
    // 验证提示
    checkAlert = (item) => {
        let { displayMode } = this.state;
        let valueLimit = item.ComponentType === 'valueLimit', // 是否是限制
            valueAndLimit = item.ComponentType === 'valueAndLimit', // 是否是值与限制
            variable = item.ComponentType === 'variable'; // 是否是变量;
        let customReg = /^(([0-9]+)|([0-9]+\.[0-9]{1,2}))$/;//非负整数,以及小数 保留2位小数
        let topNReg = /^\d+$/;//非负整数
        let StrReg = /^[0-9a-zA-Z\u4e00-\u9fa5]/;//验证非法字符 入<alert></alert>
        if (valueLimit || valueAndLimit || variable) {
            let { value, offset, limit, title } = item;
            // 是值与限制一起的数据value才有效
            if (valueAndLimit || variable) {
                if (value === '') {
                    alert(i18n.message("FILTER.ALERT.ROW.NOTEMPTY"));
                    return false
                }
                if (!Number(value) && Number(value) !== 0) { //判断是否是数字
                    alert(i18n.message("FILTER.ALERT.ROW.BENUMBER"));
                    return false
                }
                if (value < 0) { // 判断是否大于零
                    alert(i18n.message("FILTER.ALERT.ROW.THANZERO"));
                    return false
                }
                if (!topNReg.test(value)) {
                    alert(i18n.message("FILTER.ALERT.ROW.NOTOFIXED"));
                    return false;
                }
                if (Number(offset) !== NaN) {
                    if (Number(value) < Number(offset)) {
                        alert(i18n.message("FILTER.ALERT.ROW.MORETHANMIN"));
                        return false
                    }
                }
                if (!Number(limit) && Number(limit) !== 0) {
                    if (Number(value) > Number(limit)) {
                        alert(i18n.message("FILTER.ALERT.ROW.LESSTHANMAX"));
                        return false
                    }
                }
            }
            // 最大值和最小值判断
            if (!variable) {
                if (offset === '') {
                    alert(i18n.message("FILTER.ALERT.ROW.NOTEMPTY"));
                    return { name: 'offset' }
                } else {
                    if (!Number(offset) && Number(offset) !== 0) {
                        // 最小值
                        alert(i18n.message("FILTER.ALERT.ROW.MINISNUM"));
                        return { name: 'offset' }
                    }
                    if (offset < 0) {
                        // 最小值
                        alert(i18n.message("FILTER.ALERT.ROW.MINTHANZERO"));
                        return { name: 'offset' }
                    }
                }
                if (limit === '') {
                    alert(i18n.message("FILTER.ALERT.ROW.NOTEMPTY"));
                    return { name: 'limit' }
                } else {
                    if (!Number(limit) && Number(limit) !== 0) {
                        // 最大值
                        alert(i18n.message("FILTER.ALERT.ROW.MAXISNUM"));
                        return { name: 'limit' }
                    }
                    if (limit < 0) {
                        // 最大值
                        alert(i18n.message("FILTER.ALERT.ROW.MAXTHANZERO"));
                        return { name: 'limit' }
                    }
                }
                if (Number(limit) !== NaN && Number(offset) !== NaN) {
                    if (Number(limit) <= Number(offset)) {
                        alert(i18n.message("FILTER.ALERT.ROW.MAXTHANMIN"));
                        return { name: 'limit' }
                    }
                }
            }

        } else {
            let { value, order, title } = item;
            if (value === '') {
                // 标题,名称,注释不验证空
                if (item.manageStyle !== 'UNIT' && item.manageStyle !== 'NAME' && item.manageStyle !== 'TITLE' && item.manageStyle !== 'NOTES' && item.ComponentType !== 'unitConversion') {
                    alert(i18n.message("FILTER.ALERT.ROW.NOTEMPTY"));
                    return false
                }
            }
            else if ((item.manageStyle === 'NAME' || item.manageStyle === 'TITLE' || item.manageStyle === 'NOTES') && !StrReg.test(value)) {
                alert(i18n.message("ENTITY_MANAGE.NEWENTITY.ERRORFORMAT"));
                return false;
            }

        }
        return true
    }
    // 提交验证
    checkData = (data) => {
        let mark = false,
            returnObj = {
                flag: true
            };
        if (data.length) {
            for (let ind = 0; ind < data.length; ind++) {
                let item = data[ind];
                /*输入框类型*/
                /*限制值类型*/
                /*变量*/
                /*输入的单位*/
                /*注释*/
                /*value值和限制值*/
                if (item.ComponentType === 'input' || item.ComponentType === 'valueLimit' || item.ComponentType === 'variable' || item.ComponentType === 'unitConversion' || item.ComponentType === 'notes' || item.ComponentType === 'valueAndLimit') {
                    // 输入框类型(名称，值，限制，单位[输入类型])
                    let checkObj = this.checkAlert(item);
                    if (checkObj) {
                        if (checkObj.name) {
                            returnObj = {
                                flag: false,
                                index: ind,
                                name: checkObj.name
                            };
                            break;
                        }
                    } else {
                        returnObj = {
                            flag: false,
                            index: ind
                        };
                        break;
                    }

                } else if (item.ComponentType === 'btn') { //item.ComponentType === 'selectAndButton' ||
                    if (!item.options || !item.options.length) {
                        alert(i18n.message("FILTER.ALERT.ROW.ADDSWITCH"));
                        returnObj = {
                            flag: false,
                            index: ind,
                            name: 'transfrom'
                        };
                        break;
                    }
                }
            }
        }
        return returnObj
    }
    // 确定事件
    ok = (component, type) => {
        if (component === 'submitOk') {
            let { ok, uuid, updateSecondVariables } = this.props,
                newState = jtools.clone(this.state),
                { displayMode, addCombinationIndex, addCombinationIsShow, unitIndex, secondVariablesClone } = newState,
                submitObj = newState[displayMode];
            if (displayMode === 'subsection') { // 分段组件有两行有options
                if (submitObj.items[1].options.length) {
                    submitObj.items[1].options.forEach((item, index) => {
                        submitObj.items[1].options[index].show = false;
                    });
                    submitObj.items[1].options[0].show = true;
                }
                if (submitObj.items[2].options.length) {
                    submitObj.items[2].options.forEach((item, index) => {
                        submitObj.items[2].options[index].show = false;
                    });
                    submitObj.items[2].options[0].show = true;
                }
            } else if (displayMode !== 'flowRatio' && displayMode !== 'transfer') {
                if (submitObj.items[unitIndex].options.length) {
                    submitObj.items[unitIndex].options.forEach((item, index) => {
                        submitObj.items[unitIndex].options[index].show = false;
                    });
                    submitObj.items[unitIndex].options[0].show = true;
                }
            }
            if (displayMode === 'subsection' && addCombinationIndex === '1') {
                if (submitObj.items[2].options.length < 2) {
                    alert(i18n.message("FILTER.ALERT.ROW.MUSTBETWO"));
                    return;
                }
            }
            let { SortVariables } = this.state;
            let submitFlag = this.checkData(submitObj.items || {});
            if (!submitFlag.flag) {
                if (submitFlag.name === 'offset') {
                    submitObj.items[submitFlag.index].redBorder2 = true;
                } else if (submitFlag.name === 'limit') {
                    submitObj.items[submitFlag.index].redBorder3 = true;
                } else if (submitFlag.name !== 'transfrom') {
                    submitObj.items[submitFlag.index].redBorder = true;
                }
                this.setState({ [displayMode]: submitObj });
                return;
            }
            if (displayMode === 'flowRatio') {
                let selected = submitObj.items[1].options.find(item => item.isSelectd) || false,
                    selectedValue = selected ? selected.value : submitObj.items[1].options[0].value;
                submitObj.items[3].value = selectedValue;
            }
            // 数据没有错误的情况下去掉红色的边框
            submitObj.items.forEach((item, i) => {
                submitObj.items[i].order = i;
                if (item.redBorder !== undefined) {
                    submitObj.items[i].redBorder = false;
                }
                if (item.redBorder2 !== undefined) {
                    submitObj.items[i].redBorder2 = false;
                }
                if (item.redBorder3 !== undefined) {
                    submitObj.items[i].redBorder3 = false;
                }
            });
            let valItem = submitObj.items.find(item => item.manageStyle === 'VALUE');
            valItem && (valItem.name = uuid);
            ok && ok({
                newMode: displayMode,
                ...submitObj,
                uuidObj: {
                    name: uuid,
                    value: valItem ? valItem.value : '',
                    type: displayMode.toUpperCase(),
                    quoteNum: 0
                },
                SortVariables,
                newSecondVariablesClone: secondVariablesClone
            });
            // 提交之后恢复到默认
            this.setState({
                ...this.reset
            });
        } else if (component === 'alertOk') {
            let { displayMode, addCombinationIndex, alertComponent } = this.state,
                submitObj = this.state[displayMode];
            if (displayMode === 'subsection' && addCombinationIndex === '1') {
                if (submitObj.items[2].options.length < 2) {
                    alert(i18n.message("FILTER.ALERT.ROW.MUSTBETWO"));
                    return;
                }
                else{
                    let{items}=submitObj;
                    let len = items[2].options.length - 1;
                    items[2].options=items[2].options.map((it,index)=>{
                        let o=it.item[1].options.find(d1=>d1.show)||null;
                        it.item[1].options=items[1].options.map((da,i)=>{
                            if(o&&o.key===da.key){
                                da.show=true;
                            }
                            else{
                                da.show=false;
                            }
                            return jtools.extend(true,{},da);
                        });
                        if (index < len) {
                            let o1=it.item[0].options.find(d1=>d1.show)||null;
                            it.item[0].options=items[1].options.map((da,i)=>{
                                if(o1&&o1.key===da.key){
                                    da.show=true;
                                }
                                else{
                                    da.show=false;
                                }
                                return jtools.extend(true,{},da);
                            });
                        }
                        return it;
                    });
                    submitObj.items=items;
                }
            } else if (displayMode === 'flowRatio') {
                submitObj.items[1].options.map((item, index) => {
                    item.order = index;
                    item.defaultValue = item.value;
                    if (index === 0) {
                        submitObj.items[1].value = item.key;
                        submitObj.items[1].defaultValue = item.key;
                        submitObj.items[3].value = item.value;
                        submitObj.items[3].defaultValue = item.value;
                    }
                    return item;
                });
            }
            else if (displayMode === 'subsection') {
                alertComponent[displayMode][1].items[4].options.map((it, ind) => {
                    it.order = ind;
                    it.show = false;
                    if (ind === 0) {
                        it.show = true;
                    }
                    return it;
                });
                alertComponent[displayMode][1].items[9].options.map((it, ind) => {
                    it.order = ind;
                    it.show = false;
                    if (ind === 0) {
                        it.show = true;
                    }
                    return it;
                });
            }
            else if (displayMode === 'time' || displayMode === 'sort' || displayMode === 'inclination') {
                submitObj.items[2].options.map((item, index) => {
                    item.order = index;
                    item.defaultValue = item.value;
                    if (index === 0) {
                        submitObj.items[2].value = item.value;
                        submitObj.items[2].defaultValue = item.value;
                    }
                    return item;
                });
            } else if (displayMode === 'custom') {
                submitObj.items[5].options.map((item, index) => {
                    item.order = index;
                    if (index === 0) {
                        submitObj.items[5].value = item.key;
                        submitObj.items[5].defaultValue = item.key;
                    }
                    return item;
                });
                let formula = submitObj.items[5].options[0] ? (submitObj.items[5].options[0].formula || '${value}*1') : '${value}*1';
                let rval = formula.replace('${value}', submitObj.items[3].rawValue || 0);
                submitObj.items[3].value = eval(rval);
            }
            this.setState({ [type]: false, [displayMode]: submitObj, alertComponent });
        }
    }
    // 输入框得到焦点事件
    inputFoucs = (index, name, areaName) => {
        let data = jtools.clone(this.state), { displayMode, alertComponent, addCombinationIndex } = data,
            dataObj = data[displayMode];
        if (areaName === 'AddCombination') {
            if (displayMode === 'subsection') {
                alertComponent[displayMode][addCombinationIndex].items[index][name] = false;
            } else {
                alertComponent[displayMode].items[index][name] = false;
            }
            this.setState({ alertComponent })
        } else {
            dataObj.items[index][name] = false;
            this.setState({ [displayMode]: dataObj });
        }
    }
    // 复选框点击事件
    checkBoxClick = (index, areaName) => {
        let { displayMode, alertComponent } = this.state;
        alertComponent[displayMode].items[index].show = !alertComponent[displayMode].items[index].show;
        this.setState({ alertComponent });
    }
    //编辑item 
    editAlertComponent = (cloneAlertComponent) => {
        let { alertComponent, subsection, displayMode, addCombinationIndex } = this.state;
        if (displayMode === "subsection") {
            cloneAlertComponent[displayMode][1].items[4].options = subsection.items[1].options;
            cloneAlertComponent[displayMode][1].items[9].options = subsection.items[1].options;
        }
        this.setState({
            alertComponent: cloneAlertComponent
        });
    }
    render() {
        let {
            tableList, //表
            fieldList, //字段
            processMode, // 处理模式
            alertComponent, // 添加单位，关联的数据
            displayMode, // 选中模块的type
            choiceRow, // 切换模块行
            addUnitName, // 转换单位&关联的名称
            addUnitValue, // 转换单位&关联的值
            addExpression, // 转换单位的表达式
            unitIndex, // 有转换单位的索引值
            linkIndex, // 关联模块的索引值
            addCombinationIsShow, // 添加单位，关联是否显示
            addUnitIsShow, // 转换单位模块是否显示
            addLinkIsShow, // 关联模块是否显示
            randomVariable, // 随机变量
            randomVariable2, // 随机变量
            addCombinationIndex = 0, // 添加组合模块的索引值
        } = this.state;
        let choiceData = this.state[displayMode] || {},
            trueIndex = unitIndex || 0;
        let unitArr = choiceData.items ? (choiceData.items[trueIndex].options || []) : [],
            alertComponentArr = choiceData.items ? (choiceData.items[linkIndex || 0].options || []) : [],
            selectLinkValue = choiceData.items ? (choiceData.items[trueIndex].selectLinkValue || '') : '',
            choiceRowConfig = { ...choiceRow },
            addCombinationData = alertComponent[displayMode] || {};
        choiceRowConfig.optionFunc = this.choiceComponent;
        choiceRowConfig.selectValue = displayMode;
        // 事件 optionFunc : 下拉框选择事件
        return (
            <div className='FilterAlertComponentContainer'>
                <div className='FilterAlertComponent'>
                    <RowComponent
                        {...choiceRowConfig}
                        uuid={this.props.uuid}
                        areaName='choiceRow'
                        displayMode={displayMode} />
                    <RowComponent
                        {...processMode}
                        optionFunc={this.choiceComponent}
                        displayMode={displayMode}
                        areaName='processMode' /> {choiceData.items
                            ? choiceData.items.map((item, index) => {
                                return (<RowComponent
                                    uuid={this.props.uuid}
                                    key={index}
                                    index={index}
                                    {...item}
                                    inputFoucs={this.inputFoucs}
                                    changeInput={this.changeInput}
                                    alertUnitComponent={this.alertUnitComponent}
                                    displayMode={displayMode}
                                    optionFunc={this.choiceComponent} />)
                            })
                            : null}
                    {displayMode === 'custom'
                        ? <RowComponent
                            {...tableList}
                            optionFunc={this.choiceComponent}
                            displayMode={displayMode}
                            areaName='table' />
                        : ''}
                    {displayMode === 'custom'
                        ? <RowComponent
                            {...fieldList}
                            optionFunc={this.choiceComponent}
                            displayMode={displayMode}
                            areaName='field' />
                        : ''}
                    <SubmitComponent component='submit' ok={this.ok} cancle={this.cancle} /> {addCombinationIsShow
                        ? <AddCombination
                            editAlertComponent={this.editAlertComponent}
                            reset={this.reset}
                            addCombinationIndex={addCombinationIndex}
                            data={addCombinationData}
                            randomVariable={randomVariable}
                            randomVariable2={randomVariable2}
                            displayMode={displayMode}
                            addUnit={this.addUnit}
                            inputFoucs={this.inputFoucs}
                            addUnitName={addUnitName}
                            addUnitValue={addUnitValue}
                            checkBoxClick={this.checkBoxClick}
                            addExpression={addExpression}
                            optionFunc={this.choiceComponent}
                            unitArr={unitArr}
                            selectValue={selectLinkValue}
                            index={linkIndex}
                            cancle={this.cancle}
                            ok={this.ok}
                            deleUnit={this.deleUnit}
                            changeInput={this.changeInput} />
                        : null}
                </div>
            </div>
        )
    }
}
// 行组件
class RowComponent extends Component {
    displayMode = () => {
        let {
            displayMode, uuid, //变量值
            index, // 索引值
            ComponentType, // 展示类型,默认为输入框
            inputHalf, // 输入框是否是外框的一半
            selectHalf, // 下拉框是否是外框的一半
            optionFunc, // 下拉框点击事件
            options, // 下拉数据\
            unitOptions,
            rawValue,
            value, // 输入框的值1（最小值，一般的输入值）
            offset, // 输入框的值2（默认值，单位）
            limit, // 输入框的值（最大值）
            placeholder, // 输入框没有输入时显示的值（最小值，一般的输入值）
            placeholder2, // 输入框没有输入时显示的值（默认值，单位）
            placeholder3, // 输入框没有输入时显示的值（最大值）
            selectValue, // 下拉框选中的值
            changeInput, //输入框值改变事件
            inputFoucs, // 输入框得到焦点事件
            addCombinationIndex, // 添加组合的索引值
            alertUnitComponent, // 单位转换模块控制事件
            redBorder = false, // 默认值是否是红色边框(三个输入框的情况)
            redBorder2 = false, // 最小值是否是红色边框(三个输入框的情况)
            redBorder3 = false, // 最大值是否是红色边框(三个输入框的情况)
            areaName = '', // 区域名称
            manageStyle = '', // 区域名称
        } = this.props;
        if (ComponentType === 'input') {
            return <div><Input
                areaName={areaName}
                valueName='value'
                borderName='redBorder'
                redBorder={redBorder}
                index={index}
                inputHalf={inputHalf}
                inputFoucs={inputFoucs}
                value={value}
                changeInput={changeInput}
                placeholder={placeholder} /></div>;
        } else if (ComponentType === 'select') {
            return <div><SelectComponent
                areaName={areaName}
                index={index}
                optionFunc={optionFunc}
                selectArr={unitOptions || options}
                selectValue={selectValue || value}
                selectHalf={selectHalf} /></div>;
        } else if (ComponentType === 'selectAndInput') {
            return (
                <div>
                    <SelectComponent
                        areaName={areaName}
                        index={index}
                        optionFunc={optionFunc}
                        selectArr={unitOptions || options}
                        selectValue={selectValue}
                        selectHalf={selectHalf} />
                    <Input
                        redBorder={redBorder}
                        areaName={areaName}
                        valueName='value'
                        index={index}
                        inputHalf={inputHalf}
                        borderName='redBorder'
                        inputFoucs={inputFoucs}
                        value={value}
                        changeInput={changeInput}
                        placeholder={placeholder} />
                </div>
            );
        } else if (ComponentType === 'selectAndButton') {
            let style = { width: '48%', marginRight: '4%' };
            return (
                <div>
                    <SelectComponent
                        areaName={areaName}
                        style={style}
                        index={index}
                        optionFunc={optionFunc}
                        selectArr={unitOptions || options}
                        selectValue={selectValue}
                        selectHalf={selectHalf} />
                    <AddButtonComponent type='addCombinationIsShow' clickFunc={alertUnitComponent} />
                </div>
            );
        } else if (ComponentType === 'btn') {
            return (
                <div>
                    <AddButtonComponent
                        type='addCombinationIsShow'
                        addCombinationIndex={addCombinationIndex}
                        clickFunc={alertUnitComponent}
                        areaName={areaName} />
                </div>
            );
        } else if (ComponentType === 'checkBox') {
            return <CheckBox index={index} areaName={areaName} />;
        } else if (ComponentType === 'variable') {
            let valueName = (displayMode === 'custom' && index === 3) ? 'rawValue' : 'value';
            let uuidstr = '${' + uuid + '}', maxLength = 10;
            return (
                <div>
                    <span className='makeUID' title={uuidstr}>{jtools.ellipsis(uuidstr, 11)}</span>
                    <Input
                        maxLength={maxLength}
                        areaName={areaName}
                        redBorder={redBorder}
                        valueName={valueName}
                        index={index}
                        inputHalf={inputHalf}
                        borderName='redBorder'
                        inputFoucs={inputFoucs}
                        value={(displayMode === 'custom' && index === 3) ? rawValue : value}
                        changeInput={changeInput}
                        placeholder={placeholder} />
                </div>
            );
        } else if (ComponentType === 'unitConversion') {
            let styleDiv1 = { display: 'flex' },
                selectStyle = { width: '48%', marginRight: '4%' };
            return <div style={styleDiv1}>
                <SelectComponent
                    areaName={areaName}
                    index={index}
                    style={selectStyle}
                    optionFunc={optionFunc}
                    selectArr={unitOptions || options}
                    selectValue={selectValue}
                    selectHalf={selectHalf} />
                <Input
                    redBorder={redBorder}
                    areaName={areaName}
                    valueName='value'
                    index={index}
                    inputHalf={inputHalf}
                    borderName='redBorder'
                    inputFoucs={inputFoucs}
                    value={value}
                    changeInput={changeInput}
                    placeholder={placeholder} />
            </div>;
        } else if (ComponentType === 'valueLimit') {
            let styleDiv = { display: 'flex' },
                style = { marginRight: '4%' },
                maxLength = 10;
            return (
                <div style={styleDiv}>
                    <Input
                        maxLength={maxLength}
                        areaName={areaName}
                        redBorder={redBorder2}
                        valueName='offset'
                        style={style}
                        index={index}
                        inputFoucs={inputFoucs}
                        borderName='redBorder2'
                        inputHalf={inputHalf}
                        value={offset}
                        changeInput={changeInput}
                        placeholder={placeholder2} />
                    <Input
                        maxLength={maxLength}
                        areaName={areaName}
                        redBorder={redBorder3}
                        valueName='limit'
                        index={index}
                        inputFoucs={inputFoucs}
                        borderName='redBorder3'
                        inputHalf={inputHalf}
                        value={limit}
                        changeInput={changeInput}
                        placeholder={placeholder3} />
                </div>
            );
        } else if (ComponentType === 'valueAndLimit') {
            let styleDiv = { display: 'flex' },
                input1Style = { width: '32%', marginRight: '2%' },
                input2Style = Object.assign({}, input1Style, { marginRight: 0 }),
                maxLength = 10;
            return (
                <div style={styleDiv}>
                    <Input
                        maxLength={maxLength}
                        areaName={areaName}
                        redBorder={redBorder}
                        valueName='value'
                        style={input1Style}
                        index={index}
                        inputFoucs={inputFoucs}
                        borderName='redBorder'
                        inputHalf={inputHalf}
                        value={value}
                        changeInput={changeInput}
                        placeholder={placeholder} />
                    <Input
                        maxLength={maxLength}
                        areaName={areaName}
                        redBorder={redBorder2}
                        valueName='offset'
                        style={input1Style}
                        index={index}
                        inputFoucs={inputFoucs}
                        borderName='redBorder2'
                        inputHalf={inputHalf}
                        value={offset}
                        changeInput={changeInput}
                        placeholder={placeholder2} />
                    <Input
                        maxLength={maxLength}
                        areaName={areaName}
                        redBorder={redBorder3}
                        valueName='limit'
                        style={input2Style}
                        index={index}
                        inputFoucs={inputFoucs}
                        borderName='redBorder3'
                        inputHalf={inputHalf}
                        value={limit}
                        changeInput={changeInput}
                        placeholder={placeholder3} />
                </div>
            );
        }
    }
    // 行组件
    render() {
        let ComponentTypeArr = [
            'input', // 输入框
            'select', // 下拉
            'selectAndInput', // 下拉和输入框
            'selectAndButton', // 下拉和按钮
            'checkBox', // 复选框
            'unitConversion', // 单位转换输入框
            'valueLimit', // 三个输入框限制输入值
            'btn', // 编辑按钮
            'variable', // 变量
            'valueAndLimit', // 三个输入框
            'flowRatio', //流量占比
            'inclination', //倾向
            'subsection', //分段
        ], { ComponentType, title } = this.props;

        if (ComponentTypeArr.indexOf(ComponentType) >= 0) {
            return (
                <div className='RowComponent'>
                    <div title={title}>{title}：</div>
                    {this.displayMode()}
                </div>
            );
        } else {
            return (
                <div className='RowComponent'>
                    i18n.message("FILTER.ALERT.ROW.NOTWIDGET")
                </div>
            );
        }

    }
}
// 输入框组件
class Input extends Component {
    render() {
        let {
            maxLength = 200,
            inputHalf = false,
            value = '',
            placeholder = '',
            style,
            changeInput,
            BlurInput = () => { },
            index,
            valueName = 'value',
            redBorder,
            inputFoucs,
            borderName = 'redBorder',
            areaName, // input 所在区域名称
            disable
        } = this.props,
            styles = style
                ? Object.assign({}, { width: inputHalf ? '48%' : '100%' }, style)
                : { width: inputHalf ? '48%' : '100%' };
        return (<input
            maxLength={maxLength}
            title={placeholder}
            className={redBorder ? 'redBorder inputComponent' : 'inputComponent'}
            type='text'
            disabled={disable ? disable : false}
            onFocus={() => { inputFoucs && inputFoucs(index, borderName, areaName) }}
            style={styles}
            onChange={(e) => { changeInput && changeInput(e.target, index, valueName, areaName) }}
            onBlur={(e) => { BlurInput && BlurInput(e.target, index, valueName) }}
            placeholder={placeholder}
            value={value} />);
    }
}
// 下拉框组建
class SelectComponent extends Component {
    render() {
        let {
            selectHalf, // 宽度是否是该行的一半
            selectArr, //每一行的下拉列表
            optionFunc, // 下拉事件
            index, // 每一行的索引
            selectValue, // 选中的值的value
            style, // 样式
            areaName, // 模块区域
        } = this.props,
            styles = style
                ? style
                : {
                    width: selectHalf ? '48%' : '100%',
                    margin: selectHalf ? '0 4% 0 0' : '0'
                },
            selected = (selectValue && selectValue !== '') ? selectValue : (selectArr.length ? selectArr[0].value : '');
        // }
        return (
            <select
                className='selectComponent'
                style={styles}
                value={selected}
                onChange={(e) => {
                    optionFunc(e.target, index, areaName)
                }}>
                {selectArr && selectArr.map((item, i) => {
                    return (
                        <option key={i} value={item.key || item.value}>{item.name || item.key}</option>
                    )
                })}
            </select>
        )
    }
}
// + 添加按钮
class AddButtonComponent extends Component {
    render() {
        let { clickFunc, type, addCombinationIndex } = this.props;
        return (
            <button
                className='AddButtonComponent'
                onClick={() => {
                    clickFunc && clickFunc('add', type, addCombinationIndex)
                }}>{i18n.message("FILTER.ALERT.ROW.EDIT")}</button>
        )
    }
}
// 复选框
class CheckBox extends Component {
    render() {
        let {
            tips,
            index,
            areaName,
            clickFunc,
            isCheck = false
        } = this.props;
        return (
            <div className='checkBox'>
                <input type='checkbox' checked={isCheck} onClick={() => { clickFunc && clickFunc(index, areaName) }} />
                <span>{tips}</span>
            </div >
        )
    }
}
// 提交模块
class SubmitComponent extends Component {
    render() {
        let {
            style,
            cancle,
            type = '',
            ok,
            component
        } = this.props;
        return (
            <div className='SubmitComponent' style={style}>
                <ButtonComponent
                    clickFunc={ok}
                    component={`${component}Ok`}
                    type={type}
                    value={i18n.message("FILTER.ALERT.ROW.OK")} />
                <ButtonComponent
                    clickFunc={cancle}
                    component={`${component}Cancle`}
                    type={type}
                    value={i18n.message("FILTER.ALERT.ROW.CANCEL")} />
            </div>
        )
    }
}
// 按钮组件
class ButtonComponent extends Component {
    render() {
        let { value, clickFunc, type, component } = this.props;
        return (
            <button className='btnComponent' onClick={() => { clickFunc(component, type) }}>{value}</button>
        )
    }
}

// 添加关联，单位组合模块
class AddCombination extends Component {
    constructor(props) {
        super(props);
        this.state = {
            isEdit: false,
            isEditIndex: 0,
            iArray:{
                preVarible:true,
                nextVarible:true
            }//add zd
        };
    }
    componentWillReceiveProps = (newProps, newState) => {
    }
    //add zd
    onChangeCheckBox = (index,flag) => {
        let iArray =this.state.iArray;
        let iflag = !flag;
        iArray[index] = iflag
        this.setState({
            iArray
        })
    }
    //end 
    getComponent = (item, index, displayMode) => {
        let {
            optionFunc, // 下拉框点击事件
            options, // 下拉数据
            selectValue, // 下拉框选中的值
            changeInput, //输入框值改变事件
            inputFoucs, // 输入框得到焦点事件
            randomVariable, // 随机变量
            randomVariable2, // 随机变量
            checkBoxClick, // 复选框点击事件
        } = this.props;
        let { isEditIndex, isEdit } = this.state;
        switch (item.ComponentType) {
            case 'input':
                {
                    let maxLength = null;
                    if ((displayMode === 'custom' || displayMode === 'flowRatio' || displayMode === 'subsection') && item.submitType === 'value') {
                        maxLength = 10;
                    }
                    else if ((displayMode === 'inclination' || displayMode === 'subsection') && (item.submitType.includes('Value') || item.submitType.includes('Offset') || item.submitType.includes('Limit'))) {
                        maxLength = 10;
                    }
                    let obj = <div className='unitChildMethod' key={index}>
                        {item.title !== '' ? <label>{item.title}</label> : null}
                        <Input areaName='AddCombination'
                            maxLength={maxLength}
                            valueName='value'
                            borderName='redBorder'
                            disable={item.disable ? item.disable : false}//zd item.disable change false
                            index={index}
                            redBorder={item.redBorder || false}
                            inputHalf={item.inputHalf || false}
                            inputFoucs={inputFoucs}
                            value={item.value}
                            changeInput={changeInput}
                            placeholder={item.placeholder || ''} />
                    </div>;
                    return item.display === 'hide' ? null : obj;
                }
            case 'select':
                {
                    let optionsList = item.unitOptions || item.options;
                    return item.display === 'hide' ? null
                        : <div className='unitChildMethod' key={index}>
                            {item.title !== '' ? <label>{item.title}</label> : null}
                            <SelectComponent
                                areaName='AddCombination'
                                index={index}
                                optionFunc={optionFunc}
                                selectArr={optionsList.sort(SortAsc)}
                                selectValue={item.selectValue || ''}
                                selectHalf={item.selectHalf || false} />
                        </div>;
                }
            case 'textArea':
                {
                    return item.display === 'hide' ? null
                        : <div className='unitChildMethod' key={index}>
                            {item.title !== '' ? <label>{item.title}</label> : null}
                            <Input
                                areaName='AddCombination'
                                valueName='value'
                                borderName='redBorder'
                                index={index}
                                redBorder={item.redBorder || false}
                                inputHalf={item.inputHalf || false}
                                inputFoucs={inputFoucs}
                                value={item.value || ''}
                                changeInput={changeInput}
                                placeholder={item.placeholder || ''} />
                        </div>;
                }
            case 'checkbox':
                {
                    return item.display === 'hide'
                        ? null
                        : <div className='unitChildMethod' key={index}>
                            <CheckBox
                                tips={item.title}
                                clickFunc={checkBoxClick}
                                isCheck={item.show}
                                index={index}
                                areaName="AddCombination" />
                        </div>;
                }
            case 'label':
                {

                    let style = { width: '100%' };
                    let iFlag = this.state.iArray[item.submitType] ?this.state.iArray[item.submitType]: false;//add zd
                    randomVariable = (item.submitType.indexOf('next') >= 0) ? randomVariable2 : randomVariable;
                    if (isEdit) { randomVariable = item.value; }
                    return item.display === 'hide' ? null
                        : <div className='unitChildMethod' key={index}>
                            {item.title !== '' ? <label>{item.title}</label> : null}
                            {/* add zd 分段的时候添加单选框*/}
                            {displayMode==='subsection'&&(item.submitType=='nextVarible'?<i className={iFlag ? 'checked' : ''} onClick={(e) => { this.onChangeCheckBox(item.submitType,iFlag) } }></i>:'')}
                            {/* end */}
                            <p className='makeUID' style={style} title={randomVariable}>{jtools.ellipsis(randomVariable, 11)}</p>
                        </div>;
                }
            default:
                return null;
        }
    }
    editItem = (item, index, addCombinationIndex) => {
        let { displayMode, data, reset: { alertComponent }, editAlertComponent, unitArr } = this.props;
        let { isEditIndex, isEdit } = this.state;
        let editItemData = displayMode === 'subsection' ? data[addCombinationIndex].items : (data.items || []);
        let cloneAlertComponent = jtools.clone(alertComponent);
        if (isEdit && isEditIndex === index) {
            isEdit = false;
            if (displayMode === 'subsection') {
                data[addCombinationIndex] = cloneAlertComponent[displayMode][addCombinationIndex];
                if (addCombinationIndex === '1') {
                    let firstObj = unitArr.find((it => it.position === 'first'));
                    let lastObj = unitArr.find((it => it.position === 'last'));
                    if (firstObj && !lastObj) {
                        cloneAlertComponent[displayMode][addCombinationIndex].items[0].display = 'hide';
                        cloneAlertComponent[displayMode][addCombinationIndex].items[1].display = 'hide';
                        cloneAlertComponent[displayMode][addCombinationIndex].items[2].display = 'hide';
                        cloneAlertComponent[displayMode][addCombinationIndex].items[3].display = 'hide';
                        cloneAlertComponent[displayMode][addCombinationIndex].items[4].display = 'hide';
                    }
                }
            }
            else {
                data = cloneAlertComponent[displayMode];
            }
            editAlertComponent(cloneAlertComponent);
        }
        else {
            isEdit = true;
            if (displayMode === 'subsection' && addCombinationIndex === '1') {
                editItemData[1].redBorder = false;
                editItemData[2].redBorder = false;
                editItemData[3].redBorder = false;
                editItemData[6].redBorder = false;
                editItemData[7].redBorder = false;
                editItemData[8].redBorder = false;
                editItemData[0].display = item.position === 'last' ? 'hide' : '';
                editItemData[1].display = item.position === 'last' ? 'hide' : '';
                editItemData[2].display = item.position === 'last' ? 'hide' : '';
                editItemData[3].display = item.position === 'last' ? 'hide' : '';
                editItemData[4].display = item.position === 'last' ? 'hide' : '';
                editItemData[0].value = item.position === 'last' ? '' : item.item[0].variable;
                editItemData[1].value = item.position === 'last' ? '' : item.item[0].offset;
                editItemData[2].value = item.position === 'last' ? '' : item.item[0].value;
                editItemData[3].value = item.position === 'last' ? '' : item.item[0].limit;
                editItemData[4].selectValue = item.position === 'last' ? '' : item.item[0].options.find(it => it.show).key;
                editItemData[5].value = item.item[1].variable;
                editItemData[6].value = item.item[1].offset;
                editItemData[7].value = item.item[1].value;
                editItemData[8].value = item.item[1].limit;
                editItemData[9].selectValue = item.item[1].options.find(it => it.show).key;
            }
            else if (displayMode === "custom" || (displayMode === 'subsection' && addCombinationIndex === '0')) {
                editItemData[0].value = item.key;
                editItemData[1].value = item.value;
                editItemData[2].value = item.formula || '${value}*1';
            }
            else if (displayMode === "time") {
                editItemData[0].value = item.key;
                editItemData[1].selectValue = item.value;
            }
            else if (displayMode === "sort") {
                editItemData[0].value = item.key;
                editItemData[1].value = item.value;
            }
            else if (displayMode === "flowRatio") {
                editItemData[0].value = item.key;
                editItemData[1].value = item.value;
                editItemData[2].value = item.dimSql;
                editItemData[3].value = item.name;
                editItemData[4].show = item.show;
            }
            else if (displayMode === "inclination") {
                editItemData[0].value = item.preVarible;
                editItemData[1].value = item.preOffset;
                editItemData[2].value = item.preValue;
                editItemData[3].value = item.preLimit;
                editItemData[4].selectValue = item.preOperation;
                editItemData[5].value = item.name;
                editItemData[6].selectValue = item.nextOperation;
                editItemData[7].value = item.nextVarible;
                editItemData[8].value = item.nextOffset;
                editItemData[9].value = item.nextValue;
                editItemData[10].value = item.nextLimit;
            }
        }
        this.setState({ isEdit, isEditIndex: index });
    }
    deleItem = (index, mark) => {
        this.props.deleUnit(index, mark, (flag) => {
            !flag && this.setState({ isEdit: false });
        });
    }
    addUnit = (iArray) => {
        let { isEditIndex, isEdit} = this.state;
        this.props.addUnit(isEdit, isEditIndex,iArray);
    }
    okFun = (component, type) => {
        let { displayMode, data, reset: { alertComponent }, editAlertComponent } = this.props;
        let cloneAlertComponent = jtools.clone(alertComponent);
        this.props.ok(component, type);
        editAlertComponent(cloneAlertComponent);
    }
    cancelFun = (component, type) => {
        let { displayMode, data, reset: { alertComponent }, editAlertComponent } = this.props;
        let cloneAlertComponent = jtools.clone(alertComponent);
        this.props.cancle(component, type);
        cloneAlertComponent[displayMode] = data;
        editAlertComponent(cloneAlertComponent);
    }
    render() {
        let {
            data,
            displayMode, // 模块key值
            changeInput, // 改变输入框值的方法
            addUnitName, // 添加的名称
            selectValue, // 选中的关联值
            unitArr, // 添加的关联列表
            addUnit, // 添加关联事件
            deleUnit, // 删除添加关联事件
            cancle, // 取消事件
            ok, // 确定事件
            optionFunc, // 下拉框事件
            randomVariable, // 随机变量 randomVariable={randomVariable}
            randomVariable2, // 随机变量
            addCombinationIndex, // 组合模块的索引值
            reset: { alertComponent },
        } = this.props;
        let { isEditIndex, isEdit ,iArray} = this.state;
        let itemData = displayMode === 'subsection' ? data[addCombinationIndex].items : (data.items || []);
        
        return (
            <div className='AddUnitComponent'>
                <div className='unitComponent'>
                    <div>{itemData.length && itemData.map((item, index) => {
                        return this.getComponent(item, index, displayMode)
                    })}</div>
                    <div className='addUnitBtn'>
                        <SnowAddBtn type='link' clickFunc={this.addUnit} iArray={this.state.iArray}/>
                    </div>
                    <div>
                        {unitArr && unitArr.length
                            ? unitArr.sort(SortAsc).map((item, index) => {
                                return (<UnitChild
                                    editItem={this.editItem}
                                    deleUnit={this.deleItem}
                                    key={index}
                                    name={item.key}
                                    item={item}
                                    index={index}
                                    displayMode={displayMode}
                                    addCombinationIndex={addCombinationIndex}
                                    isEditIndex={isEditIndex}
                                    isEdit={isEdit}
                                    iArray={iArray}//zd
                                    mark='unit' />)
                            })
                            : null}
                    </div>
                </div>
                <SubmitComponent
                    type='addCombinationIsShow'
                    component='alert'
                    ok={this.okFun}
                    cancle={this.cancelFun} />
            </div>
        )
    }
}

// 添加单位的列表
class UnitChild extends Component {
    render() {
        let {
            isEditIndex,
            isEdit,
            name,
            value,
            deleUnit,
            index,
            mark = '',
            displayMode,
            addCombinationIndex,
            item,
            editItem,
            iArray
        } = this.props;
        let styles = (isEdit && isEditIndex === index) ? 'current' : 'unitChild';
        return (
            <div className={styles} value={value} title={name} >
                <div onClick={(e) => { editItem(item, index, addCombinationIndex) }}>
                    {((displayMode === 'subsection' && addCombinationIndex === '1') || displayMode === 'inclination')
                        ? <Subsection displayMode={displayMode} data={item} iArray={iArray} />
                        : jtools.ellipsis(name, 10)}
                </div>
                <DeleBtn clickFunc={deleUnit} index={index} mark={mark} />
            </div>
        )
    }
}
// 分段组件
class Subsection extends Component {
    getComponent = () => {
        let { data, displayMode,iArray } = this.props,
            returnComponent;
        if (displayMode === 'subsection') {
            if (data && data.item && data.item.length) {
                returnComponent = data.item.map((item, index) => {
                    // let m = (index === data.item.length - 1) ? '' : '~';
                    let m=''
                    if((index !== data.item.length - 1)){
                        if(data.item[0].value!==undefined&&data.item[1].value!==undefined){
                            m='~'
                        }else{
                            m=''
                        }
                    }else{
                        m=''
                    }
                    let unitObj = item.options && (item.options.find(it => it.show === true) || { key: item.options.length ? item.options[0].key : '' });
                    // return (
                    //     <div key={index}>
                    //         {item.value !== undefined
                    //             ? <div style={{ display: 'inline' }}>
                    //                 <span title={item.value}>{jtools.ellipsis(item.value, 5)}</span>
                    //                 <span title={unitObj.key}>{jtools.ellipsis(unitObj.key, 5)}</span>
                    //                 <span>{m}</span>
                    //             </div>
                    //             : '>'}
                    //     </div>
                    // )
                    if(item.options!==undefined){
                        if(item.value!==undefined){
                            return (
                                <div key={index}>
                                    {item.value !== undefined
                                        ? <div style={{ display: 'inline' }}>
                                            <span title={item.value}>{jtools.ellipsis(item.value, 5)}</span>
                                            <span title={unitObj.key}>{jtools.ellipsis(unitObj.key, 5)}</span>
                                            <span>{m}</span>
                                        </div>
                                        : ''}
                                </div>
                            )
                        }
                    }else{
                            return (
                                <div key={index}>
                                    {item.value !== undefined
                                        ? <div style={{ display: 'inline' }}>
                                            <span title={item.value}>{jtools.ellipsis(item.value, 5)}</span>
                                            <span title={unitObj.key}>{jtools.ellipsis(unitObj.key, 5)}</span>
                                            <span>{m}</span>
                                        </div>
                                        : '>'}
                                </div>
                            )
                    }
                    
                });
            }
        } else if (displayMode === 'inclination') {
            returnComponent = <div>
                <span title={data.preValue}>{jtools.ellipsis(data.preValue, 5)}</span>
                <span title={data.preOperation}>{jtools.ellipsis(data.preOperation, 12)}</span>
                <span title={data.name}>{jtools.ellipsis(data.name, 5)}</span>
                <span title={data.nextOperation}>{jtools.ellipsis(data.nextOperation, 12)}</span>
                <span title={data.nextValue}>{jtools.ellipsis(data.nextValue, 5)}</span>
            </div>;
        }
        return returnComponent;
    }
    render() {
        let { data, displayMode } = this.props;
        return (
            <div className='Subsection'>
                {this.getComponent()}
            </div>
        )
    }
}

// 删除的小按钮
class DeleBtn extends Component {
    render() {
        let {
            clickFunc,
            index,
            mark = ''
        } = this.props;
        return (
            <button className='DeleBtn' onClick={() => { clickFunc && clickFunc(index, mark) }}>×</button>
        )
    }
}
// 箭头添加按钮
class SnowAddBtn extends Component {
    render() {
        
        let { clickFunc,iArray } = this.props;
        return (
            <button className='SnowAddBtn' onClick={() => { clickFunc && clickFunc(iArray) }}></button>
        )
    }
}
