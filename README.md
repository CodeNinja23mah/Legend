# Legend
Investifynigeria 
import React, { useState, useEffect } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button";

const Dashboard = () => { const [walletBalance, setWalletBalance] = useState(0); const [totalInvestment, setTotalInvestment] = useState(0); const [referrals, setReferrals] = useState([]); const [xp, setXp] = useState(0); const [level, setLevel] = useState(1); const [dailyReturnClaimed, setDailyReturnClaimed] = useState(false);

useEffect(() => { // Simulated initial data load setWalletBalance(300); // welcome bonus setTotalInvestment(0); setReferrals(["08123456789"]); setXp(0); setLevel(1); }, []);

const claimDailyReturn = () => { if (!dailyReturnClaimed) { const returnAmount = totalInvestment * 0.25; setWalletBalance(walletBalance + returnAmount); setXp(xp + 10); setDailyReturnClaimed(true); } };

return ( <div className="p-4 grid gap-4"> <h1 className="text-xl font-bold">Welcome to Investify Nigeria</h1>

<Card>
    <CardContent className="p-4">
      <p><strong>Wallet Balance:</strong> ₦{walletBalance.toLocaleString()}</p>
      <p><strong>Total Investment:</strong> ₦{totalInvestment.toLocaleString()}</p>
    </CardContent>
  </Card>

  <Card>
    <CardContent className="p-4">
      <p><strong>XP:</strong> {xp}</p>
      <p><strong>Level:</strong> {level}</p>
    </CardContent>
  </Card>

  <Card>
    <CardContent className="p-4">
      <p className="font-semibold mb-2">Your Referrals:</p>
      <ul className="list-disc list-inside">
        {referrals.map((ref, i) => (
          <li key={i}>{ref}</li>
        ))}
      </ul>
    </CardContent>
  </Card>

  <Button
    onClick={claimDailyReturn}
    disabled={dailyReturnClaimed || totalInvestment === 0}
  >
    {dailyReturnClaimed ? "Daily Return Claimed" : "Claim Daily Return"}
  </Button>
</div>

); };

export default Dashboard;

