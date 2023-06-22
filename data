run functions.py

### nodes on list nodes, rules of each node on list rules, regulators of each node on dict regs, total of perturbations on list pert ###

nodes = ['DSB', 'ATM', 'yH2AX', 'NHEJCore', 'H2AK15_H4K20', 'OTRO', 'SHLD', 'c_NHEJ', 'TRIP13', 'BRCA1FANCS', 'MRN_CtIP', 'TIP60', 'sRES', 'EXO1', 'lRES', 'RAD51', 'HR', 'PARP1', 'POLQ', 'MMEJ', 'RAD52', 'SSA'] 
rules= '(DSB|SHLD)&!(sRES|c_NHEJ|HR|MMEJ|SSA);(DSB|MRN_CtIP|yH2AX)&!(c_NHEJ|HR|MMEJ|SSA);((DSB&(ATM|NHEJCore))|(sRES|lRES));(DSB|SHLD)&!(sRES|c_NHEJ|HR|MMEJ|SSA);(((yH2AX&NHEJCore)&!(TIP60))|(H2AK15_H4K20&OTRO))&!(c_NHEJ|HR|MMEJ|SSA);((DSB|SHLD)&H2AK15_H4K20)&!(BRCA1FANCS);(OTRO&yH2AX&sRES)&!(TRIP13|(sRES&POLQ)|c_NHEJ|HR|MMEJ|SSA);((NHEJCore&OTRO)|c_NHEJ)&!(sRES|HR|MMEJ|SSA);(yH2AX&DSB)&!(MRN_CtIP|c_NHEJ|HR|MMEJ|SSA);(DSB&ATM)&!(OTRO|c_NHEJ|HR|MMEJ|SSA);(DSB&(ATM|c_NHEJ)&(BRCA1FANCS|yH2AX))&!(sRES|lRES|(OTRO&(SHLD|NHEJCore))|c_NHEJ|HR|MMEJ|SSA|EXO1);(MRN_CtIP|sRES|lRES)&!(c_NHEJ|HR|MMEJ|SSA);(MRN_CtIP|sRES)&!(lRES|SHLD|c_NHEJ|HR|MMEJ|SSA);(ATM&sRES)&!((OTRO&NHEJCore)|SHLD|POLQ);((sRES&EXO1)|lRES)&!(HR|SSA|c_NHEJ|MMEJ);(lRES&TIP60)&!(RAD52|SHLD|POLQ|HR);((RAD51&lRES)|HR)&!(c_NHEJ|MMEJ|SSA);(((DSB&yH2AX)&!NHEJCore)|(sRES&!(MRN_CtIP|SHLD)))&!(c_NHEJ|HR|MMEJ|SSA);(PARP1&sRES)&!((sRES&SHLD)|(EXO1&sRES)|MMEJ);((PARP1&POLQ)|MMEJ)&!(c_NHEJ|HR|SSA);lRES&!(RAD51|c_NHEJ|HR|MMEJ|SSA);((lRES&RAD52)|SSA)&!(RAD51|c_NHEJ|HR|MMEJ)'
# NOTE: 53BP1 is 'OTRO'

### Regulators of each gene
regs = {}
for n in range(len(nodes)):
    nodo = nodes[n]
    regla = regla_tipo_griffin(rules.split(';')[n],nodes)
    
    reg = regla
    quitar = '()~!'
    for a in quitar:
        reg = reg.replace(a,'')
    #sacar solo los nodos y quitar repeticiones:
    reg = list(dict.fromkeys(reg.split('|')[0].split('&')))
    regs[nodo] = reg

### Total of perturbations for each node
pert = []
for a in regs:
    pert.append(2**len(regs[a]))
