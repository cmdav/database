```sql
# database
For DB things
#This sql statement help to fetch data from the table for playgroup

-- To view all members and their respective parents.

select first_name,last_name from member a inner join parents b on a.parent_id_parents = bi.parent_id;

-- To view all members for a particular event or session

select first_name,last_name from member a inner join members_registered_events b on a.member_id = b.member_id_member;

--To view all members whose parents have paid
select first_name,last_name from member where parent_id_parents in (select parent_id_parents from payments where paid_in_full = 'Y') ;

--To view all parents whose payment outstanding is above ten thousand naira
select a.parent_name,b.outstanding_amount from parents a,payments b  where a.parent_id = b.parent_id_parents AND b.outstanding_amount > 10000;

--To view all members who registered for a particular session

select a.first_name,a.last_name ,b.session_name from member a,session b, member_registered_events c where a.member_id = c.member_id_member AND
c.session_id = b.session_id;

-- To view all members registered
select * from member;

--To view all sessions and their respective teachers
select teacher_name,session_name from teachers a INNER JOIN member_registered_events b ON a.teacher_id=b.teacher_id INNER JOIN sessions c.session_id=b.session_id;

--To view the most recent payment
select amount_paid,max(date_of_payment) from payments ;

-- To view the amounts paid according to days
select amount_paid,date_of_payment from payments group by date_of_payment order by date_of_payment descending;