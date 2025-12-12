**here is the codes to create procedures**

CREATE OR REPLACE PROCEDURE Calculate_Premium(p_customer_policy_id IN NUMBER) IS
    v_premium NUMBER;
BEGIN
    SELECT Premium_amount
    INTO v_premium
    FROM POLICY p
    JOIN CUSTOMER_POLICY cp ON p.Policy_id = cp.Policy_id
    WHERE cp.Customer_policy_id = p_customer_policy_id;

    DBMS_OUTPUT.PUT_LINE('Total Premium for Customer Policy ' || p_customer_policy_id || ': ' || v_premium);
END;
