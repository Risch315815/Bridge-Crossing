# Bridge-Crossing
#solving the konigsberg bridge problem by listing every possible route
    final_result = []

#defining symbols for bridge crossing

    def bridge_crossing_rule(list):
        possible_path = []
        if list[-1] == 11:
            possible_path = [22,71]
        elif list[-1] == 12:
            possible_path = [32,42,51,21]
        elif list[-1] == 21:
            possible_path = [12,71]
        elif list[-1] == 22:
            possible_path = [32,42,51,11]
        elif list[-1] == 31:
            possible_path = [11,21,51,42]
        elif list[-1] == 32:
            possible_path = [41,62]
        elif list[-1] == 41:
            possible_path = [11,21,51,32]
        elif list[-1] == 42:
            possible_path = [31,62]
        elif list[-1] == 51:
            possible_path = [61,72]
        elif list[-1] == 52:
            possible_path = [11,21,32,42]
        elif list[-1] == 61:
            possible_path = [31,41]
        elif list[-1] == 62:
            possible_path = [52,72]
        elif list[-1] == 71:
            possible_path = [52,61]
        elif list[-1] == 72:
            possible_path = [12,22]
        return possible_path

#checking if path had been repeated

    def check_repeat(list):
        repeat_check = []
        for i in list:
            repeat_check.append(int(i/10))
        if len(repeat_check) != len(set(repeat_check)):
            return False

    for i in [11,12,21,22,31,32,41,42,51,52,61,62,71,72]:
        route = [i]
        next_step1 = bridge_crossing_rule(route)
        for i in next_step1:
            route1 = route + [i]
            if check_repeat(route1) == False:
                #print(route1[0:-1])
                final_result.append(route1[0:-1])
                continue
            else:
                next_step2 = bridge_crossing_rule(route1)
                for i in next_step2:
                    route2 = route1 + [i]
                    if check_repeat(route2) == False:
                        #print(route2[0:-1])
                        final_result.append(route2[0:-1])
                        continue
                    else:
                        next_step3 = bridge_crossing_rule(route2)
                        for i in next_step3:
                            route3 = route2 + [i]
                            if check_repeat(route3) == False:
                                #print(route3[0:-1])
                                final_result.append(route3[0:-1])
                                continue
                            else:
                                next_step4 = bridge_crossing_rule(route3)
                                for i in next_step4:
                                    route4 = route3 + [i]
                                    if check_repeat(route4) == False:
                                        #print(route4[0:-1])
                                        final_result.append(route4[0:-1])
                                        continue
                                    else:
                                        next_step5 = bridge_crossing_rule(route4)
                                        for i in next_step5:
                                            route5 = route4 + [i]
                                            if check_repeat(route5) == False:
                                                #print(route5[0:-1])
                                                final_result.append(route5[0:-1])
                                                continue
                                            else:
                                                next_step6 = bridge_crossing_rule(route5)
                                                for i in next_step6:
                                                    route6 = route5 + [i]
                                                    if check_repeat(route6) == False:
                                                        #print(route6[0:-1])
                                                        final_result.append(route6[0:-1])
                                                        continue
                                                    else:
                                                        next_step7 = bridge_crossing_rule(route6)
                                                        for i in next_step7:
                                                            route7 = route6 + [i]
                                                            if check_repeat(route7) == False:
                                                                #print(route7[0:-1])
                                                                final_result.append(route7[0:-1])
                                                                continue
#data processing

    workingList = final_result
    def compare_item_length(lista):
        final_res = []
        for i in lista:
            #print(i)
            temp_route1 = i
            temp_route2 = i
            for j in lista:
                if temp_route1[0:3] == j[0:3]:
                    if len(temp_route1) < len(j):
                        temp_route1 = j
                        temp_route2 = j
                    elif len(temp_route1) == len(j):
                        temp_route2 = j
                    else:
                        continue
            if temp_route1 == temp_route2:
                final_res.append(temp_route1)
            else:
                final_res.append(temp_route1)
                final_res.append(temp_route2)

        print(final_res)
        print(type(final_res))
        finlist = [list(x) for x in {(tuple(e)) for e in final_res}]
        print(finlist)
        return finlist

        print(compare_item_length(workingList))
        finfinlist = []
        for item in compare_item_length(workingList):
            if item not in finfinlist:
                finfinlist.append(item)
        print(finfinlist)

        with open ('all_popssible_route002.txt', 'w') as f:
            f.write(str(finfinlist))
            f.close()
 
